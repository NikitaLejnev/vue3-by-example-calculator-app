<template>
  <ion-page>
    <ion-header translucent>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title>Home</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content fullscreen>
      <div id="container">
        <ion-list>
          <ion-item v-for="(h, index) of historyWithTypes" :key="h.id">
            <ion-label v-if="h.type === 'tip'">
              Tip Calculation - Subtotal: {{ h.subtotal }}, Country:
              {{ h.country }}
            </ion-label>
            <ion-label v-else>
              Currency Conversion - Amount {{ h.amount }},
              {{ h.fromCurrency }} to {{ h.toCurrency }}
            </ion-label>
            <ion-button @click="go(h)">Open</ion-button>
            <ion-button @click="deleteEntry(index)">Delete</ion-button>
          </ion-item>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>
