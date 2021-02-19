<template>
  <ion-page>
    <ion-header>
      <Toolbar />
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Player</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <div>
        <div class="music-art">
          <img src="https://images.complex.com/complex/images/c_fill,dpr_auto,f_auto,q_90,w_1400/fl_lossy,pg_1/yzngxkrdpaq86pfbzryh/davido-a-better-time-stream" />
        </div>

        <div class="song-title-artist">
          <div class="song-title">
            Holy Ground (feat Nicki Minaj)
          </div>
          <div class="artist-name">
            Davido
          </div>
        </div>

        <div class="song-timeline">
          <ion-range v-model="songTimelineCurrentValue" :max="songTimelineMaxValue" @ionChange="updateSongCurrentPosition()" ref="timeline"></ion-range>

          <div class="song-timeline-minutes">
            <ion-grid>
              <ion-row>
                <ion-col size="2" class="song-timer">
                  {{songCurrentTime}}
                </ion-col>
                
                <ion-col size="2" offset="8" class="song-timer ion-text-end">
                  {{songDuration}}
                </ion-col>
              </ion-row>
            </ion-grid>
          </div>
        </div>

        <div class="player-controls">
          <ion-grid>
            <ion-row>
              <ion-col size="2">
                <ion-icon :icon="playSkipBack" class="play-control" />
              </ion-col>

              <ion-col size="8" class="ion-text-center">
                <ion-icon v-if="playing" :icon="pauseCircle" class="play-button" @click="play()" />
                <ion-icon v-else :icon="playCircle" class="play-button" @click="play()" />
              </ion-col>
              
              <ion-col size="2" class="ion-text-start">
                <ion-icon :icon="playSkipForward" class="play-control" />
              </ion-col>
            </ion-row>
          </ion-grid>
          
          <audio ref="audio" src="assets/Ara.mp3"></audio>
        </div>
       
      </div>
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonRange, IonGrid, IonCol, IonRow, IonIcon } from '@ionic/vue';
import Toolbar from '@/components/Toolbar.vue';
import { playSkipBack, playSkipForward, playCircle, pauseCircle } from 'ionicons/icons';


export default  {
  name: 'Player',
  components: { Toolbar, IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonRange, IonGrid, IonCol, IonRow, IonIcon  },
  data(){
    return {
      playing: false,
      songTimelineCurrentValue: 0,
      songTimelineMaxValue : 100,
      songCurrentTime: "0:00",
      songDuration: "0:00"
    }
  },
  created(){
    console.log(this.$refs);

    setInterval(this.updatesongTimelineCurrentValue, 500)
  },
  setup() {
    return {
      playSkipBack,
      playSkipForward,
      playCircle,
      pauseCircle
    }
  },
  watch : {
    songTimelineCurrentValue: function (val) {
      if(val == this.songTimelineMaxValue){
        this.playing = false
      }
    }
  },
  methods : {
    play(){
      console.log(this.$refs.audio)
      let song = this.$refs.audio;

      this.songDuration = this.formatSongTime(song.duration);
      if(this.playing){
        this.playing = false;
        song.pause()
      }else{
        this.playing = true;
        song.play()
      }
      
    },

    updatesongTimelineCurrentValue(){
      let song = this.$refs.audio;
      let timeline = this.$refs.timeline;

      if(song && timeline){
        /* console.log(song.duration);
        console.log(song.currentTime); */
        //timeline.max = song.duration;
        this.songTimelineMaxValue = song.duration;
        this.songTimelineCurrentValue = song.currentTime;
        this.songCurrentTime = this.formatSongTime(song.currentTime);

        
      }
      
    },

    updateSongCurrentPosition(){
      let song = this.$refs.audio;
      
      /* console.log(this.songTimelineCurrentValue)
      console.log(song.currentTime) */
      let timeDiff = this.songTimelineCurrentValue - song.currentTime;
      if(Math.abs(timeDiff) >= 1){
        console.log("Changed song position")
        song.currentTime = this.songTimelineCurrentValue;
      }
      
    },
    formatSongTime(seconds){
      let min = Math.floor((seconds/60));
      let sec = Math.floor(seconds - (min *60));

      if(sec < 10){
        sec = `0${sec}`;
      }

      return `${min}:${sec}`;
    }
  }
}
</script>

<style scoped>
.music-art{
  width: 80%;
  margin-top: 20px;
  margin-right: auto;
  margin-left: auto;
  height: 300px;
}

.song-title-artist{
  text-align: center;
  margin-top: 10px;
}

.song-title{
  font-size: 1.2em;
  font-weight: bold;
  font-family: Arial;
}

.artist-name{
  font-size: 0.9em;
  margin-top: 5px;
}

.song-timeline {
  width: 90%;
  margin-right: auto;
  margin-left: auto;
}

.song-timeline-minutes{
  margin-top: -25px;
}

.song-timer{
  font-size: 0.8em;
}

.player-controls {
  width: 50%;
  margin-right: auto;
  margin-left: auto;
}

.play-button{
  font-size: 86px;
  margin-top: -30px;
}

.play-control{
  font-size: 24px;
}
</style>