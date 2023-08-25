---
comments: true
---

# About

Recently, giscus hit GitHub API's rate limit for one of its users. One of the causes was that giscus always requested a new token from GitHub whenever it makes an API call for unauthenticated users. Each token is valid for 60 minutes, but I didn't cache it at all. As giscus is serverless, I hadn't set up a database (it didn't need one 🤷). Thus, I didn't have a proper place to cache the tokens.

I thought I could get away by always requesting a fresh token, but unfortunately that wasn't the case. Unusually high traffic would lead giscus to request new tokens too many times in an hour, hitting the rate limit. I decided to set up a database to cache the tokens.

I don't make any money off giscus, so free tiers are a life-saver for the project. After a quick research, I found several serverless database platforms with free tiers:

PlanetScale: 3 free databases, with 10GB storage, 100 million rows read/month, and 10 million rows written/month per database.
Fauna: 100k read ops, 50k write ops, 500k compute ops, 5GB storage.
Upstash: 10k commands/day, 100k commands/month, 1GB storage.
Supabase: unlimited API requests, 500MB storage.