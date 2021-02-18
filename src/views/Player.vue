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
      
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import Toolbar from '@/components/Toolbar.vue';

export default  {
  name: 'Player',
  components: { Toolbar, IonHeader, IonToolbar, IonTitle, IonContent, IonPage }
}
</script>