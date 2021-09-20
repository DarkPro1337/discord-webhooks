---
title: "Spotify"
date: 2018-07-25T00:33:47+03:00
weight: 10
draft: false
---
## if `New saved track` then `Make a web request`

```json
{
  "embeds": [{
    "color": 2021216,
    "title": "New song added!",
    "thumbnail": {
      "url": "{{AlbumCoverURL}}"
    },
    "fields":[
      {
        "name": "Track",
        "value": "[{{TrackName}}]({{TrackURL}})",
        "inline": true
      },
      {
        "name": "Artist",
        "value": "{{ArtistName}}",
        "inline": true
      },
      {
        "name": "Album",
        "value": "{{AlbumName}}",
        "inline": true
      }
    ],
    "footer": {
      "text": "Added {{SavedAt}}",
      "icon_url": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/200px-Spotify_logo_without_text.svg.png"
    }
  }]
}
```

![](../img/spotify-basic.png)
