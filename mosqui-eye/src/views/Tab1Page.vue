<template>
  <ion-page :class="{ 'dark-mode': isDarkMode }">
    <ion-menu side="start" content-id="main-content">
      <ion-header>
        <ion-toolbar>
          <ion-title>Menu</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content>
        <ion-list>
          <ion-item>Dashboard</ion-item>
          <ion-item>Map Location</ion-item>
          <ion-item>Scheduler</ion-item>
          <ion-item>Settings</ion-item>
          <ion-item>About</ion-item>
        </ion-list>
      </ion-content>
    </ion-menu>

    <div id="main-content">
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-menu-button></ion-menu-button>
          </ion-buttons>
          <ion-title>Home</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content :fullscreen="true">
        <ion-header collapse="condense">
          <ion-toolbar>
            <ion-title size="large">Home</ion-title>
          </ion-toolbar>
        </ion-header>

        <ion-grid>
          <ion-row>
            <ion-col size="12" size-md="6">
              <ion-card>
                <ion-card-header>
                  <ion-card-title>Welcome to MosquiEye</ion-card-title>
                </ion-card-header>
                <ion-card-content>
                  This is your home page. Explore the features and enjoy your stay!
                </ion-card-content>
              </ion-card>
            </ion-col>
            <ion-col size="12" size-md="6">
              <ion-card>
                <ion-card-header>
                  <ion-card-title>Get Started</ion-card-title>
                </ion-card-header>
                <ion-card-content>
                  Click the button below to get started with our application.
                  <ion-button expand="full" color="primary">Get Started</ion-button>
                  <ion-button expand="full" color="secondary" @click="toggleDarkMode">
                    {{ isDarkMode ? 'Disable Dark Mode' : 'Enable Dark Mode' }}
                  </ion-button>
                </ion-card-content>
              </ion-card>
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-content>
    </div>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonGrid, IonRow, IonCol, IonCard, IonCardHeader, IonCardTitle, IonCardContent, IonButton, IonMenu, IonMenuButton, IonButtons, IonList, IonItem } from '@ionic/vue';

const isDarkMode = ref(false);

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value;
  document.body.classList.toggle('dark', isDarkMode.value);
};
</script>

<style>
.dark-mode {
  --ion-background-color: #000000;
  --ion-text-color: #fff;
}
</style>
