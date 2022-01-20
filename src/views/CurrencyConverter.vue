<template>
  <ion-page>
    <ion-header translucent>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title> Currency Converter </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content fullscreen>
      <div id="container">
        <ion-list>
          <ion-item>
            <ion-label :color="!amountValid ? 'danger' : undefined"> Amount to Convert </ion-label>
            <ion-input
              class="ion-text-right"
              type="number"
              v-model="amount"
              required
              placeholder="Amount"
            ></ion-input>
          </ion-item>
          <ion-item>
            <ion-label> Currency to Convert From </ion-label>
            <ion-select v-model="fromCurrency" ok-text="Okay" cancel-text="Dismiss">
              <ion-select-option :value="c.abbreviation" v-for="c of fromCurrencies" :key="c.name">
                {{ c.name }}
              </ion-select-option>
            </ion-select>
          </ion-item>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>
