<template>
  <div
    v-show="show"
    v-observe-visibility="!initialVisibleState ? {
      callback: onVisibilityChanged,
      once: true,
    } : null"
    :class="{ placeholder: !visible }"
  >
    <template
      v-if="visible"
    >
      <p
        class="videoIndex"
      >
        <font-awesome-icon
          v-if="isCurrentVideo"
          class="videoIndexIcon"
          :icon="['fas', 'play']"
        />
        <template
          v-else
        >
          {{ videoIndex + 1 }}
        </template>
      </p>
      <ft-list-video
        :data="data"
        :playlist-id="playlistId"
        :playlist-type="playlistType"
        :playlist-index="playlistIndex"
        :playlist-reverse="playlistReverse"
        :playlist-shuffle="playlistShuffle"
        :playlist-loop="playlistLoop"
        :playlist-item-id="playlistItemId"
        force-list-type="list"
        :appearance="appearance"
        :always-show-add-to-playlist-button="alwaysShowAddToPlaylistButton"
        :quick-bookmark-button-enabled="quickBookmarkButtonEnabled"
        :can-move-video-up="canMoveVideoUp"
        :can-move-video-down="canMoveVideoDown"
        :can-remove-from-playlist="canRemoveFromPlaylist"
        @pause-player="$emit('pause-player')"
        @move-video-up="$emit('move-video-up')"
        @move-video-down="$emit('move-video-down')"
        @remove-from-playlist="$emit('remove-from-playlist')"
      />
    </template>
  </div>
</template>

<script src="./ft-list-video-numbered.js" />
<style scoped src="./ft-list-video-numbered.css" />
