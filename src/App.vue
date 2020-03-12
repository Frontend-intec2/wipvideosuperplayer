<template>
  <div id="app" style=" background: black; margin: -5vw; padding: 5vw;">
    <h1
      style="color: white; font-size: 5vw; font-family: roboto; font-weight: 90; opacity: 0.2; margin-bottom: 10vw"
    >Entertaiment Player</h1>
    {{ current.title }}
    <div
      style="color: white; margin-bottom: -10vw"
      v-for="(song, index) in songs"
      v-bind:key="index"
    >{{ song.src }} - {{ index }}</div>

    <div
      v-for="(song, index) in songs"
      v-bind:key="index"
      v-bind:src="song.src"
      style="color: white; font-size: 2vw; font-family: roboto; font-weight: 90; border: red solid 2px"
    >
      {{ song.src }} - {{ index }}
      <button
        style="width:36.4vw; padding:0vw; cursor:pointer; background: none"
        class="picclick"
        @click="playIt(index)"
      >
        >
        <img
          style="border-radius: 2vw; border: white 2px solid; width: 36vw; display: block; margin-bottom: -13vw; margin-top: 25vw"
          v-bind:src="song.img"
        />

        <Media
          :src="song.src"
          :title="song.title"
          :artist="song.artist"
          :kind="'video'"
          :ref="'superplayer'"
          controls
          style="width: 30vw; height: 17vw; padding: 5vw; margin: -7vw 0vw -4vw -1vw;"
        />
      </button>

      <br />
      {{ song.src }}
      <br />
      {{ song.title }}
      <br />
      {{ song.artist }}
      <br />
    </div>
    <!--
    <div>
      <img src="./assets/prayer.jpg" />
    </div>
    <div
      style=" border: transparent 0.5vw solid; width: 30vw; height: 17vw; margin: 0 auto; display: inline-block"
    >
      <Media :kind="'video'" :src="new_src" controls autoply style="width: 30vw; height: 17vw" />
    </div>
    <div
      style="position: relative; border: transparent 0.5vw solid; width: 30vw; height: 17vw; margin: 0 auto; display: inline-block"
    >
      <img style=" position: absolute; height: 17vw; left: 6vw" src="./assets/prayer.jpg" />
      <Media
        :kind="'audio'"
        :src="new_src"
        controls
        autoply
        style=" left: 0; top: 0; position: relative; width: 30vw; height: 17vw"
      />
    </div>

    <div>
      <input
        type="text"
        @keyup.enter="changeSrc"
        v-model="new_src"
        placeholder="Enter new video src..."
      />
      <p>Example: https://archive.org/download/ElephantsDream/ed_1024_512kb.mp4</p>
    </div>-->
  </div>
</template>

<script>
import Media from "@dongido/vue-viaudio";

export default {
  name: "App",
  components: {
    Media
  },
  data() {
    return {
      current: {},
      src:
        "https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4",

      // key: 1,

      songs: [
        {
          title: "A Little Prayer",
          artist: "Aretha Franklin",
          poster: "./assets/prayer.jpg",
          src: require("./assets/prayer.mp3"),
          img: require("./assets/prayer.jpg")
          // class: "playing == true"
          // songs.src
        },
        {
          title: "Elephant's Dream",
          artist: "Dumbo",
          src: "https://archive.org/download/ElephantsDream/ed_1024_512kb.mp4"
          // img: require("./assets/mado.jpg")
        }
        // {
        //   title: "Invincible",
        //   artist: "Deaf Kev",
        //   src: "http://vjs.zencdn.net/v/oceans.mp4",
        //   type: "video/mp4",
        //   options: {
        //     autoplay: true,
        //     volume: 0.6
        //   }
        // }
      ]

      //      new_src: this.songs[this.key].src,
      //      new_img: this.songs[this.key].img
    };
  },

  methods: {
    playIt(index) {
      console.log(this.$refs.superplayer);
      this.current = this.songs[index];
      this.$refs.superplayer[index].play();

      //    this.src = this.new_src;

      //archive.org/download/ElephantsDream/ed_1024_512kb.mp4 = this.new_src;
      // https: alert(this.current.src);
    }
    // console.log(this.song.play());
    // console.log(song.src);
    // play(song) {
    //   if (typeof song.src != "undefined") {
    //     this.current = song;
    //     this.songs.src = this.current.src;
    //   }

    //   this.song.play();

    //   this.player.addEventListener(
    //     "ended",
    //     function() {
    //       this.index++;
    //       if (this.index > this.songs.length - 1) {
    //         this.index = 0;
    //       }

    //       this.current = this.songs[this.index];
    //       this.play(this.current);
    //     }.bind(this)
    //   );
    //   this.isPlaying = true;
    // }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
input {
  width: 60%;
  height: 40px;
  font-size: 16px;
}
</style>
