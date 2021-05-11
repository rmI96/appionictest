<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script lang="ts">
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';
import { OneSignal } from '@ionic-native/onesignal';

export default defineComponent({
  name: 'App',
  mounted () {
    console.log('ddddd 99000')
    OneSignal.startInit('97232021-25f1-4f97-9be2-064dc7e2cd17', '884459473522');

    OneSignal.inFocusDisplaying(OneSignal.OSInFocusDisplayOption.InAppAlert);

    OneSignal.handleNotificationReceived().subscribe((res) => {
      // do something when notification is received
      console.log(res)
    });

    OneSignal.handleNotificationOpened().subscribe((res) => {
      // do something when a notification is opened
      console.log(res)
    });

    OneSignal.endInit();
    console.log('hhhhh')
  },
  components: {
    IonApp,
    IonRouterOutlet
  }
});
</script>
