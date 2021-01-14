<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 4</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 3</ion-title>
        </ion-toolbar>
      </ion-header>

      <ExploreContainer name="Tab 4 page" />
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
import { Plugins } from '@capacitor/core'

export default  {
  name: 'Tab4',
  components: {
    ExploreContainer,
    'ion-header': IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
  },
  methods: {
    // getCurrentPosition: function() {}
    async getCurrentPosition(){
      const { Geolocation } = Plugins
      const loc = await Geolocation.getCurrentPosition()
      console.log(loc)
      // this.loc = loc
    },
    async takePicture() {
      const { Camera } = Plugins;
      console.log('Camera:')
      console.log(Camera)
      const picture = await Camera.getPhoto({});
      console.log(picture)
    },
    getNetworkStatus() {
      const { Network } = Plugins
      Network.addListener('networkStatusChange', (status) => {
        console.log("Network status changed", status)
      })
    }
  },
  async mounted() {
    await this.getCurrentPosition()
    // await this.takePicture()
    await this.getNetworkStatus()
  }
}
</script>
