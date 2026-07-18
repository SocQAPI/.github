<p align="center">
  <a href="https://socq.ai">
    <img src="./assets/header.png" alt="SocQ social media scraping API" />
  </a>
</p>

<p align="center">
  <a href="https://socq.ai"><img src="https://img.shields.io/badge/Website-socq.ai-F64C31?style=for-the-badge" alt="SocQ website" /></a>
  <a href="https://docs.socq.ai"><img src="https://img.shields.io/badge/API%20Docs-docs.socq.ai-111827?style=for-the-badge" alt="SocQ API documentation" /></a>
  <a href="https://socq.ai/apis"><img src="https://img.shields.io/badge/API%20Catalog-Explore-2563EB?style=for-the-badge" alt="Explore the SocQ API catalog" /></a>
  <a href="https://socq.ai/dashboard/api-key"><img src="https://img.shields.io/badge/Get%20API%20Key-Start-F64C31?style=for-the-badge" alt="Get a SocQ API key" /></a>
</p>

## Public social data, ready for your product

SocQ turns public profiles, posts, videos, comments, search results, transcripts, and engagement signals into structured records your applications can use. Authenticate with one API key, submit a collection task, and retrieve normalized results through a consistent REST workflow.

## What you can collect

| Data type | Available data |
| --- | --- |
| **Profiles & identity** | Public profiles, creator accounts, pages, follower counts, and account metadata |
| **Posts & media** | Posts, Reels, videos, Shorts, transcripts, captions, and engagement signals |
| **Comments & feedback** | Public comments and available conversation metadata |
| **Search & discovery** | Profile, video, keyword, and hashtag discovery, depending on the endpoint |

[Explore the live API Catalog](https://socq.ai/apis) for current endpoint and platform availability.

## How SocQ works

1. Call a data collection endpoint with your Bearer API key.
2. Store the returned `task_id`. New tasks start in the `queued` state.
3. Query `GET /v1/tasks/{task_id}` as the task moves through `queued`, `running`, `succeeded`, or `failed`.
4. After success, read normalized records from `results.items` and continue with `results.next_cursor` when another page is available.
5. Add `callback_url` when you need a completion notification. Callback delivery is best-effort, so polling remains the fallback.
6. Download compressed raw JSONL data from `GET /v1/tasks/{task_id}/files` when you need the source records in bulk.

## Built for social data workflows

- **Social listening:** Collect public discussions, content, and feedback.
- **Social analytics:** Analyze content, audience, and engagement signals.
- **Creator intelligence:** Research creators, their content, and public performance.
- **Brand monitoring:** Follow brands, competitors, and market activity.

## Quickstart

Create an [API key](https://socq.ai/dashboard/api-key), then submit an Instagram profile search:

```bash
curl -X POST "https://api.socq.ai/v1/instagram/search" \
  -H "Authorization: Bearer $SOCQ_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "sustainable travel",
    "results_limit": 25
  }'

# Save task_id from the submit response, then query the task.
curl "https://api.socq.ai/v1/tasks/$TASK_ID?limit=50" \
  -H "Authorization: Bearer $SOCQ_API_KEY"
```

Successful task responses contain normalized records in `data.results.items`. Pass `data.results.next_cursor` back as the `cursor` query parameter to read the next page.

SocQ is built for public data workflows. It is not an official API of the social platforms represented in its catalog and does not provide access to private account data.

## Public examples

[`SocQAPI/socq-examples`](https://github.com/SocQAPI/socq-examples) is the
canonical directory for all 32 focused API repositories.

| Instagram | Facebook | YouTube | TikTok | X |
| --- | --- | --- | --- | --- |
| [Posts](https://github.com/SocQAPI/instagram-posts-api) | [Pages](https://github.com/SocQAPI/facebook-pages-api) | [Channels](https://github.com/SocQAPI/youtube-channels-api) | [Profiles](https://github.com/SocQAPI/tiktok-profiles-api) | [Profiles](https://github.com/SocQAPI/twitter-profile-scraper-api) |
| [Comments](https://github.com/SocQAPI/instagram-comments-api) | [Posts](https://github.com/SocQAPI/facebook-posts-api) | [Videos](https://github.com/SocQAPI/youtube-videos-api) | [Videos](https://github.com/SocQAPI/tiktok-videos-api) | [Posts](https://github.com/SocQAPI/twitter-tweet-scraper-api) |
| [Followers Count](https://github.com/SocQAPI/instagram-followers-count-api) | [Comments](https://github.com/SocQAPI/facebook-comments-api) | [Channel Videos](https://github.com/SocQAPI/youtube-channel-videos-api) | [Comments](https://github.com/SocQAPI/tiktok-comments-api) | [User Posts](https://github.com/SocQAPI/twitter-user-tweets-scraper-api) |
| [Reels](https://github.com/SocQAPI/instagram-reels-api) |  | [Comments](https://github.com/SocQAPI/youtube-comments-api) | [Search](https://github.com/SocQAPI/tiktok-search-api) | [Search](https://github.com/SocQAPI/twitter-search-api) |
| [Search](https://github.com/SocQAPI/instagram-search-api) |  | [Shorts](https://github.com/SocQAPI/youtube-shorts-api) | [Hashtags](https://github.com/SocQAPI/tiktok-hashtags-api) |  |
|  |  | [Search](https://github.com/SocQAPI/youtube-search-api) |  |  |
|  |  | [Transcripts](https://github.com/SocQAPI/youtube-transcript-api) |  |  |

### LinkedIn

| Profiles | Companies | Posts | Jobs |
| --- | --- | --- | --- |
| [LinkedIn Profiles API](https://github.com/SocQAPI/linkedin-profiles-api) | [LinkedIn Companies API](https://github.com/SocQAPI/linkedin-companies-api) | [LinkedIn Posts API](https://github.com/SocQAPI/linkedin-posts-api) | [LinkedIn Jobs API](https://github.com/SocQAPI/linkedin-jobs-api) |

### Reddit

| Posts | Comments | Subreddit Posts | Search |
| --- | --- | --- | --- |
| [Reddit Posts API](https://github.com/SocQAPI/reddit-posts-api) | [Reddit Comments API](https://github.com/SocQAPI/reddit-comments-api) | [Reddit Subreddit Posts API](https://github.com/SocQAPI/reddit-subreddit-posts-api) | [Reddit Search API](https://github.com/SocQAPI/reddit-search-api) |

Each repository keeps API keys server-side, implements the complete asynchronous
task and pagination flow, and uses synthetic fixtures instead of customer data.

## Developer resources

- Website: [socq.ai](https://socq.ai)
- API documentation: [docs.socq.ai](https://docs.socq.ai)
- API catalog: [socq.ai/apis](https://socq.ai/apis)
- Examples: [github.com/SocQAPI/socq-examples](https://github.com/SocQAPI/socq-examples)
- API keys: [socq.ai/dashboard/api-key](https://socq.ai/dashboard/api-key)
- Support: [support@socq.ai](mailto:support@socq.ai)
