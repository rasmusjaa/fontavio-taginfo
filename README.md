# Fontavio taginfo project file

This repository exists to serve one file: [`taginfo.json`](taginfo.json), the
[taginfo project file](https://wiki.openstreetmap.org/wiki/Taginfo/Projects)
for [Fontavio](https://fontavio.com/), listing the OpenStreetMap tags the app
reads and how each one is used.

It is fetched by taginfo from:

```
https://raw.githubusercontent.com/rasmusjaa/fontavio-taginfo/main/taginfo.json
```

## Why it is not served from fontavio.com

It was, at first. fontavio.com sits behind Cloudflare with Bot Fight Mode on,
which issues a managed challenge to requests from datacenter IP ranges. A
browser gets the file; an automated fetch from a CI runner or a server gets an
HTML challenge page instead, which is not valid JSON. Cloudflare's free plan
has no per-path exception for that setting, so the file moved somewhere with
no bot protection in front of it rather than weakening the site's.

## Changing it

Fontavio's own repository is private and holds the source of truth, at
`docs/launch/osm/taginfo.json`. When the importer starts or stops reading a
tag, update it there, copy it here, and bump `data_updated`. Taginfo refetches
on its own schedule.

Relevant OSM links:

- Project page: <https://taginfo.openstreetmap.org/projects/fontavio>
- Wiki page: <https://wiki.openstreetmap.org/wiki/Fontavio>
