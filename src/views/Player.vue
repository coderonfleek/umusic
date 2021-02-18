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
          <ion-range value="20"></ion-range>

          <div class="song-timeline-minutes">
            <ion-grid>
              <ion-row>
                <ion-col size="2" class="song-timer">
                  1:23
                </ion-col>
                
                <ion-col size="2" offset="8" class="song-timer ion-text-end">
                  2:34
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
                <ion-icon :icon="playCircle" class="play-button" />
              </ion-col>
              
              <ion-col size="2" class="ion-text-start">
                <ion-icon :icon="playSkipForward" class="play-control" />
              </ion-col>
            </ion-row>
          </ion-grid>
        </div>
       
      </div>
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonRange, IonGrid, IonCol, IonRow, IonIcon } from '@ionic/vue';
import Toolbar from '@/components/Toolbar.vue';
import { playSkipBack, playSkipForward, playCircle } from 'ionicons/icons';

export default  {
  name: 'Player',
  components: { Toolbar, IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonRange, IonGrid, IonCol, IonRow, IonIcon  },
  setup() {
    return {
      playSkipBack,
      playSkipForward,
      playCircle
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