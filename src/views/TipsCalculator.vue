<template>
  <ion-page>
    <ion-header translucent>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title>Tips Calculator</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content fullscreen>
      <div id="container">
        <form>
          <ion-list>
            <ion-item>
              <ion-label :color="!amountValid ? 'danger' : undefined">Subtotal (Local Currency)</ion-label>
              <ion-input
                class="ion-text-right"
                type="number"
                v-model="subtotal"
                required
                placeholder="Subtotal"
              ></ion-input>
            </ion-item>

            <ion-item>
              <ion-label>Country (Local Currency)</ion-label>
              <ion-select v-model="country" ok-text="Okay" cancel-text="Dismiss">
                <ion-select-option :value="c.name" v-for="c of countries" :key="c.name">{{ c.name }}</ion-select-option>
              </ion-select>
            </ion-item>

            <ion-item>
              <ion-label>Tipping Rate</ion-label>
              <ion-label class="ion-text-right">{{ tippingRate }}%</ion-label>
            </ion-item>

            <ion-item>
              <ion-button size="default" @click="calculateTip">Calculate Tip</ion-button>
            </ion-item>
          </ion-list>

          <ion-list>
            <ion-item>
              <ion-label>Tip (Local Currency)</ion-label>
              <ion-label class="ion-text-right">{{ result.tip }}</ion-label>
            </ion-item>

            <ion-item>
              <ion-label>Total (Local Currency)</ion-label>
              <ion-label class="ion-text-right">{{ result.total }}</ion-label>
            </ion-item>
          </ion-list>
        </form>
      </div>
    </ion-content>
  </ion-page>
</template>
