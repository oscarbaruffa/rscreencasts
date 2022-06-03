---
title: |
  {{screencast}}
description: |
  {{notable_topics}}
date: {{date}}
date-format: long
---

Notable topics: {{notable_topics}}

Recorded on: {{date}}

Timestamps by: {{contributor}}

[View code]({{browse_r_code_url}})

## Screencast

<div id="yt-player" data-video-id="{{vid_key}}"></div>

## Timestamps

```{=html}
<div id="topics">
{{#timestamps}}
<div class="topic">
  <h3 id="ts-{{timestamp_sec}}">
    <button class="btn btn-link btn-timestamp" onClick="playerSkipToTimestamp({{timestamp_sec}}, this)">{{timestamp_with_hours}}</button>
  </h3>
  <div class="topic_badges"><div>{{{functions}}}</div><div>{{{packages}}}</div></div>
  <div class="topic_description">{{{description}}}</div>
</div>
{{/timestamps}}
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

function playerSkipToTimestamp(seconds, tsElement) {
  player.seekTo(seconds, true)
  tsElement.scrollIntoView()
  document.getElementById("screencast").scrollIntoView()
}
</script>
