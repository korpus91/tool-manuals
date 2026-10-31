# The roadmap | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skellydocs main re-read: RoadmapPage.tsx, RoadmapContent.tsx, RoadmapEntry.tsx, githubUtils.ts (CACHE_TTL_MS, ETag/304/403 handling, extractExcerpt), collectLinkedUrls.ts, types.ts, and package.json (0.3.17); props, fetch params, filter/sort/view UI, dedupe, and excerpt rules all confirmed

2026-08-24

SkellyDocs source read directly (package at 0.3.17, main); consumer usage verified in this site's package.json, Docusaurus config, custom.css, and fetched SkellyCam docs

More about how these docs are written

# The roadmap

RoadmapPage takes a repo slug (plus optional roadmapLabel, pinnedIssues, title, projectBoardUrl) and fills itself from the GitHub API. Items reach the dashboard two ways, merged and deduplicated by issue number:

- Labeled, anything carrying the roadmap label in the repo, fetched via api.github.com with state=all and up to 100 items. The label itself is filtered out of the displayed chips.

- Pinned, any issue/PR URL referenced anywhere in the content config, collected by collectLinkedUrls and passed as pinnedIssues. Pinned items get a "pinned" badge; an item that is both labeled and pinned counts once.

Caching lives in localStorage with a five-minute TTL and ETag support: repeat visits send If-None-Match, a 304 refreshes the timestamp without refetching, and a 403 (rate limit) falls back to cached data with an error banner explaining exactly that. A Retry button clears the caches and refetches.

The UI offers free-text search across titles and excerpts, chip filters for type (issue/PR), status (open/closed), and source (labeled/pinned, only when pins exist), clickable label pills derived from the fetched items, sort by recently updated/newest/oldest, and a grid/list toggle. A collapsible "About this roadmap" section explains the mechanics, including an issues-vs-pull-requests primer aimed at non-developer readers. Card excerpts are generated from the issue body: code fences and HTML comments stripped, markdown characters removed, first two sentences capped at 280 characters.
