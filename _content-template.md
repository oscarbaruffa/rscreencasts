---
title: |
  {{ screencast }}
description: |
  {{ notable_topics }}
date: {{ strftime(date, "%F") }}
date-format: long
---

Notable topics: {{ notable_topics }}

Recorded on: {{ strftime(date, "%F") }}

Timestamps by: {{ contributor }}

[View code]({{ browse_r_code_url }})

## Full screencast

<div id="yt-player" data-video-id="{{ vid_key }}"></div>

## Timestamps

```{=html}
<div id="topics">
{{ #timestamps }}
<div class="topic">
  <h3><a onClick="playerSkipToTimestamp({{ timestamp_sec }})" href="#full-screencast">{{ timestamp_with_hours }}</a></h3>
  <div class="topic_badges"><div>{{{ functions }}}</div><div>{{{ packages }}}</div></div>
  <div class="topic_description">{{{ description }}}</div>
</div>
{{ /timestamps }}
</div>
```
     
<script>
// 2. This code loads the IFrame Player API code asynchronously.
var tag = document.createElement("script");

tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName("script")[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

// 3. This function creates an <iframe> (and YouTube player)
//    after the API code downloads.
var videoId = document.getElementById("yt-player").dataset.videoId;
var player;
function onYouTubeIframeAPIReady() {
  player = new YT.Player("yt-player", {
    height: "486",
    width: "864",
    videoId: videoId,
    playerVars: {
      "playsinline": 1
    }
  });
}

function playerSkipToTimestamp(seconds) {
  player.seekTo(seconds, true)
}
</script>
