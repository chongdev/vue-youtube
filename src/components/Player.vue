<template>
    <div>

        <div>
            <h2>Youtube Events</h2>

            <button type="button" class="btn" @click="isPlayer=true">Load Youtube</button>
        </div>
        
        <div v-if="isPlayer">
            <youtube
                :video-id="videoId"
                @ready="ready"
                @playing="playing"
                @paused="paused"
                @error="error"
                @ended="ended"
                @buffering="buffering"
                @qued="qued"
                
                :player-vars="{ autoplay: 1 }"
            ></youtube>
        </div>
    </div>
</template>

<script>
/**
 * https://www.npmjs.com/package/vue-youtube-embed
 * 
 * Props
 * These are available props.
 *
 * player-width: String or Number, default value is 640
 * player-height: String or Number, default value is 360
 * player-vars: Object, default value is {start: 0, autoplay: 0} Can also specify rel.
 * video-id: String, required
 * mute: Boolean default value is false
 * host: String default value is https://www.youtube.com. Can be set to https://www.youtube-nocookie.com as well.
 *
 * Events
 * These are the events that will be emitted by the component.
 *
 * ready
 * ended
 * playing
 * paused
 * buffering
 * qued
 * error
 *
 */

export default {
    data() {
        return {
            videoId: "G-s6Gzk_57E",

            isPlayer: false,
        };
    },

    methods: {
        ready(event) {
            this.player = event.target;

            console.log("ready", event);
        },
        ended(event){
            console.log("ended", event);
        },
        
        playing(event) {
            // this.player = event.target

            console.log("playing", event);
            // The player is playing a video.
        },
        paused(event){
            console.log("paused", event);
        },
        buffering(event){
            console.log("buffering", event);
        },
        qued(event){
            console.log("qued", event);
        },
        // change () {
        //     // when you change the value, the player will also change.
        //     // If you would like to change `playerVars`, please change it before you change `videoId`.
        //     // If `playerVars.autoplay` is 1, `loadVideoById` will be called.
        //     // If `playerVars.autoplay` is 0, `cueVideoById` will be called.
        //     this.videoId = 'another video id'
        // },
        stop() {
            this.player.stopVideo();
        },
        pause() {
            this.player.pauseVideo();
        },

        error(event) {
            console.log("error", event);
        },
    },
};
</script>