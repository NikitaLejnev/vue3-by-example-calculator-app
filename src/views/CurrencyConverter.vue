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
            <ion-label> Currency to Convert From</ion-label>
            <ion-select v-model="fromCurrency" ok-text="Okay" cancel-text="Dismiss">
              <ion-select-option :value="c.abbreviation" v-for="c of fromCurrencies" :key="c.name">
                {{ c.name }}
              </ion-select-option>
            </ion-select>
          </ion-item>

          <ion-item>
            <ion-label> Currency to Convert To</ion-label>
            <ion-select v-model="toCurrency" ok-text="Okay" cancel-text="Dismiss">
              <ion-select-option :value="c.abbreviation" v-for="c of toCurrencies" :key="c.name">
                {{ c.name }}
              </ion-select-option>
            </ion-select>
          </ion-item>

          <ion-item>
            <ion-button size="default" @click.stop="calculate"> Calculate </ion-button>
          </ion-item>
        </ion-list>

        <ion-list v-if="result">
          <ion-item>
            <ion-label>Result</ion-label>
            <ion-label class="ion-text-right">
              {{ amount }} {{ fromCurrency }} is {{ result.toFixed(2) }} {{ toCurrency }}
            </ion-label>
          </ion-item>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonButtons,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage,
  IonTitle,
  IonToolbar,
  IonSelect,
  IonInput,
  IonLabel,
  IonButton,
  IonList,
  IonItem,
  IonSelectOption,
} from "@ionic/vue";
import { computed, reactive, ref, watch } from "vue";
import { currencies as currenciesArray } from "../constants";
import axios from "axios";
import { useStore } from "vuex";
import { CurrencyConversion } from "@/interfaces";
import { v4 as uuidv4 } from "uuid";
import { useRoute } from "vue-router";

</script>
