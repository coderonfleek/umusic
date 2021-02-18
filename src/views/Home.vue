<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <Toolbar />
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Home</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-list>
        <ion-list-header>
          Your Music
        </ion-list-header>

        <ion-item>
          <ion-avatar slot="start">
            <img src="http://www.clipartbest.com/cliparts/di7/ogo/di7ogo5eT.jpg">
          </ion-avatar>
          <ion-label>
            <h2>Holy Ground</h2>
            <p>Davido</p>
          </ion-label>
        </ion-item>

        

        
      </ion-list>
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonList, IonListHeader, IonItem, IonAvatar, IonLabel } from '@ionic/vue';
import Toolbar from '@/components/Toolbar.vue';

export default  {
  name: 'Home',
  components: { Toolbar, IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonList, IonListHeader, IonItem, IonAvatar, IonLabel }
}
</script>