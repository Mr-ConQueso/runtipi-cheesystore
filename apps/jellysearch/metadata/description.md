<img src="img/icon.svg" width="150" height="150" />

# JellySearch

> [!CAUTION]
> The search may return results from libraries that the user is not authorised to view. Search results are not checked for user permissions. see https://gitlab.com/DomiStyle/jellysearch/-/issues/16

A fast full-text search proxy for Jellyfin. Integrates seamlessly with most Jellyfin clients.

## How does it work?
JellySearch keeps a separate index of the Jellyfin SQLite database inside of Meilisearch. It keeps the index in sync with Jellyfin with a cronjob.

When a search request is made by a Jellyfin client, the request is forwarded to JellySearch instead of directly to Jellyfin by the reverse proxy.

JellySearch will then search and filter by the input query in Meilisearch and forward the found items to Jellyfin, resulting in a great speed up of search queries.

On a large Jellyfin server this brings the search speed per request down from about 2 seconds to 1 - 150 milliseconds.

As an added bonus, the search is much less prone to not finding results because of typos and also supports searching across multiple fields, e.g. `mr robot`, `how to train your dragon 2010`, `queen a night at the opera`, `brotherhood fullmetal`, `better cal sual` all work.

## Requirements
* Jellyfin running inside of Docker
* Jellyfin running behind a reverse proxy
* JellySearch needs read access to the Jellyfin database

Running outside of Docker works but you're on your own right now. If you get it working feel free to put in a PR detailing how it works.

## Tested clients
### Working

* Web client
* Jellyfin for Android
* Jellyfin for Android TV
* Finamp (Android & Linux)
* Findroid
* Delfin
* Gelli
* Jellyfin Vue*

\* Works but is still pretty slow

### Currently not working

* Audio books and Live TV were not tested
* Genre searches are currently not working and are passed along directly to the Jellyfin server
* If you have an exotic client which can do filtering and searching at the same time, this will probably break things