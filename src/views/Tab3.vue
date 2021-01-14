<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 3</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 3</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-card>
        <ion-card-header>
          <ion-card-title>Login</ion-card-title>
        </ion-card-header>
        <ion-card-content>
          <ion-input type="email" placeholder="Put your user here"></ion-input>
          <ion-input type="password" placeholder="Put your password here"></ion-input>
<!--          <ion-input type="number" value="333"></ion-input>    -->

          <ion-button color="primary" @click="presentAlert">Login</ion-button>
          <ion-button color="secondary" @click="openToast">prova</ion-button>

        </ion-card-content>
      </ion-card>

      <ion-chip>
        <ion-label>Default asdasd</ion-label>
        <ion-badge color="danger">11</ion-badge>
      </ion-chip>

      <ion-item>
        <ion-badge slot="start">11</ion-badge>
        <ion-label>My Item</ion-label>
        <ion-badge slot="end">22</ion-badge>
      </ion-item>

      <ExploreContainer name="Tab 3 page" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonItem, IonBadge, IonChip, IonLabel, toastController,alertController, IonCard,IonCardHeader,IonCardContent,IonButton,IonCardTitle,IonInput, IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';

export default  {
  name: 'Tab3',
  components: {
    IonItem,
    IonBadge,
    IonChip,
    IonLabel,
    IonCard,
    IonCardHeader,
    IonCardContent,
    IonCardTitle,
    IonButton,
    ExploreContainer,
    'ion-header': IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonInput
  },
  methods: {
    async presentAlert() {
      const alert = await alertController
          .create({
            cssClass: 'my-custom-class',
            header: 'Alert',
            subHeader: 'Subtitle',
            message: 'This is an alert message.',
            buttons: ['OK'],
          });
      return alert.present();
    },
    async openToast() {
      const toast = await toastController
          .create({
            message: 'Your settings have been saved.',
            duration: 2000
          })
      return toast.present();
    },
  }
}
</script>
