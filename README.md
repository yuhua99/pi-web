# pi-web

A Pi Coding Agent extension that adds `webfetch` and `websearch` tools for web content retrieval and search.

## Features

- Extract readable Markdown from web pages with `webfetch`.
- Search the web through Exa's MCP endpoint with `websearch`.
- Fetch Reddit listings and posts, including `redd.it` short links, using a Reddit session cookie.
- Fetch X status URLs using X authentication cookies.

## Installation

```bash
pi install git:github.com/<owner>/pi-web
```

## Configuration

### Exa

`websearch` uses the Exa MCP endpoint. Set `EXA_API_KEY` to provide an Exa API key:

```bash
export EXA_API_KEY='…'
```

The variable is optional.

### Reddit

`webfetch` routes `reddit.com` and `redd.it` URLs to a Reddit-specific fetcher. Set `REDDIT_SESSION` to the value of the `reddit_session` cookie:

```bash
export REDDIT_SESSION='…' # cookie: reddit_session
```

Log in at reddit.com, open DevTools, go to **Application** → **Cookies**, and copy the `reddit_session` value.

Supported URLs include listings, posts, and short links.

### X (Twitter)

`webfetch` routes X status URLs to an X-specific fetcher. Set both cookie values:

```bash
export TWITTER_AUTH_TOKEN='…' # cookie: auth_token
export TWITTER_CT0='…'        # cookie: ct0
```

Log in at x.com, open DevTools, go to **Cookies**, and copy `auth_token` and `ct0`.

Only status URLs are supported, for example:

```text
https://x.com/user/status/123
```

Use a secondary account, and re-export cookies when they expire.
