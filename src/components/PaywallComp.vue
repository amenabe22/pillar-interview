<template>
  <div class="mb-32">
    <div>
      <div class="d1"></div>
      <div class="d2"></div>
    </div>
    <div class="flex flex-col items-center justify-center text-center mt-14">
      <p class="text-4xl font-bold headerTxt">Upgrade To Pro</p>
      <div class="flex flex-row gap-3 mt-3">
        <p class="topSelectorText">Monthly</p>
        <Switch @changed="switchChanged"></Switch>
        <p class="topSelectorText">Anually</p>
        <chip :color="'bg-emerald-400'"> Save 25% </chip>
      </div>
    </div>
    <div class="flex items-center justify-center mt-5">
      <div
        class="
          xl:grid
          md:grid-cols-2
          xl:grid-cols-3 xl:w-3/4
          mx-2
          gap-12
          relative
          hidden
          md:grid
          sm:grid
        "
      >
        <div
          style="height: 700px"
          v-for="(pl, ix) in plans"
          :key="ix"
          :class="{ 'shadow-2xl shadow-indigo-300': pl.recommended }"
          class="
            flex flex-col
            mt-4
            items-start
            paymentCard
            bg-gray-50
            rounded-3xl
          "
        >
          <div class="relative w-full">
            <div v-if="pl.recommended" class="mb-4"></div>
            <div
              :class="{
                'recommendedBorderTop bg-violet-100 border-indigo-700':
                  pl.recommended,
                'bg-gray-100': !pl.recommended,
              }"
              class="
                flex flex-col
                justify-center
                items-center
                p-6
                rounded-t-3xl
              "
            >
              <p
                class="font-bold featureTitle leading-7 text-center pb-5"
                style="color: #4624d6"
                v-text="pl.name"
              ></p>
              <div
                class="
                  flex flex-row
                  justify-center
                  items-end
                  text-gray-700
                  order-0
                "
              >
                <p
                  v-if="pl.discount"
                  class="priceDiscount font-normal"
                  v-text="`-${pl.discount}%`"
                ></p>
                <p class="priceCurrency leading-3 pb-3 px-1">$</p>
                <p
                  class="priceAmount"
                  v-text="annual ? pl.price.annual : pl.price.monthly"
                ></p>
                <p
                  class="priceCurrency leading-3 pb-4"
                  v-text="pl.cents"
                  v-if="pl.cents"
                ></p>
                <p v-text="annual ? '/year' : '/month'"></p>
              </div>

              <p class="text-gray-400 smalltxt" v-if="annual">
                Yearly Price:
                <span class="line-through" v-text="pl.offer?.annual"></span>
              </p>
              <p class="text-gray-400 smalltxt" v-else>
                Monthly Price:
                <span class="line-through" v-text="pl.offer?.monthly"></span>
              </p>
            </div>
            <div
              v-if="pl.recommended"
              class="
                absolute
                top-0
                right-0
                mx-20
                p-2
                bg-indigo-700
                mb-1
                text-white
                rounded-lg
              "
            >
              <p class="font-bold text-xl">Recommended</p>
            </div>
          </div>

          <div
            :class="{
              recommendedBorderBtm: pl.recommended,
            }"
            class="
              rounded-b-3xl
              flex flex-col
              items-center
              justify-between
              order-1
              innerBox
              self-stretch
              grow
              pt-9
              pr-6
              pb-2
              bg-gray-50
            "
          >
            <div class="flex flex-col items-center p-3 text-center gap-6">
              <p
                v-for="(ft, i) in pl.features"
                :key="i"
                class="text-center featureTxt text-gray-700 font-normal"
                v-text="ft"
              ></p>
            </div>
            <div class="flex flex-col items-center order-0 gap-4">
              <p
                class="text-indigo-700 text-center bottomTagline text-xs"
                v-if="pl.bottomTagline"
                v-text="pl.bottomTagline"
              ></p>
              <!-- TODO: set accurate dimensions for button -->
              <button
                class="
                  flex flex-col
                  justify-center
                  items-center
                  w-32
                  h-10
                  text-center
                  rounded-lg
                "
                :class="{
                  'text-white bg-indigo-700': pl.darkBtn,
                  'bg-gray-200': !pl.darkBtn,
                }"
                v-text="pl.buttonLabel"
              ></button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div>
      <div
        class="
          flex flex-col
          bg-white
          m-auto
          p-auto
          xl:hidden
          lg:hidden
          md:hidden
          sm:hidden
        "
      >
        <div class="flex overflow-x-scroll pb-10 hide-scroll-bar">
          <div class="flex flex-nowrap lg:ml-40 md:ml-20">
            <div class="flex overflow-x-scroll pb-10 hide-scroll-bar">
              <div
                style="height: 700px"
                v-for="(pl, ix) in plans"
                :key="ix"
                :class="{ 'shadow-2xl shadow-indigo-400': pl.recommended }"
                class="
                  flex flex-col
                  mt-4
                  w-screen
                  items-start
                  paymentCard
                  bg-gray-50
                  rounded-3xl
                "
              >
                <div class="relative w-full">
                  <div v-if="pl.recommended" class="mb-4"></div>
                  <div
                    :class="{
                      'recommendedBorderTop bg-violet-100 border-indigo-700':
                        pl.recommended,
                      'bg-gray-100': !pl.recommended,
                    }"
                    class="
                      flex flex-col
                      justify-center
                      items-center
                      p-6
                      gap-5
                      rounded-t-3xl
                    "
                  >
                    <p
                      class="font-bold featureTitle leading-7 text-center pb-5"
                      style="color: #4624d6"
                      v-text="pl.name"
                    ></p>
                    <div
                      class="
                        flex flex-row
                        justify-center
                        items-end
                        text-gray-700
                        order-0
                      "
                    >
                      <p
                        v-if="pl.discount"
                        class="priceDiscount font-normal"
                        v-text="`${pl.discount}%`"
                      ></p>
                      <p class="priceCurrency leading-3 pb-3 px-1">$</p>
                      <p
                        class="priceAmount"
                        v-text="annual ? pl.price.annual : pl.price.monthly"
                      ></p>
                      <p
                        class="priceCurrency leading-3 pb-4 px-1"
                        v-text="pl.cents"
                        v-if="pl.cents"
                      ></p>
                      <p>/month</p>
                    </div>
                    <p class="text-gray-400 smalltxt" v-if="annual">
                      Yearly Price:
                      <span
                        class="line-through"
                        v-text="pl.offer?.annual"
                      ></span>
                    </p>
                    <p class="text-gray-400 smalltxt" v-else>
                      Monthly Price:
                      <span
                        class="line-through"
                        v-text="pl.offer?.monthly"
                      ></span>
                    </p>
                  </div>

                  <div
                    v-if="pl.recommended"
                    class="
                      absolute
                      top-2
                      mx-20
                      right-0
                      p-2
                      left-0
                      bg-indigo-700
                      text-white
                      rounded-lg
                    "
                  >
                    <p class="font-bold text-xl text-center">Recommended</p>
                  </div>
                </div>

                <div
                  :class="{
                    recommendedBorderBtm: pl.recommended,
                  }"
                  class="
                    rounded-b-3xl
                    flex flex-col
                    items-center
                    justify-between
                    order-1
                    innerBox
                    self-stretch
                    grow
                    pt-9
                    pr-6
                    pb-2
                    bg-gray-50
                  "
                >
                  <div class="flex flex-col items-center p-3 text-center gap-6">
                    <p
                      v-for="(ft, i) in pl.features"
                      :key="i"
                      class="text-center featureTxt text-gray-700 font-normal"
                      v-text="ft"
                    ></p>
                  </div>
                  <div class="flex flex-col items-center order-0 gap-4">
                    <p
                      class="text-indigo-700 text-center bottomTagline text-xs"
                      v-if="pl.bottomTagline"
                      v-text="pl.bottomTagline"
                    ></p>
                    <button
                      class="
                        flex flex-col
                        justify-center
                        items-center
                        w-32
                        h-10
                        text-center
                        rounded-lg
                      "
                      :class="{
                        'text-white bg-indigo-700': pl.darkBtn,
                        'bg-gray-200': !pl.darkBtn,
                      }"
                      v-text="pl.buttonLabel"
                    ></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import Chip from "./Chip.vue";
import Switch from "./Switch.vue";

interface Price {
  monthly: number;
  annual: number;
}

interface Plans {
  name: string;
  price: Price;
  cents?: number | null;
  discount?: number | null;
  features: Array<string>;
  buttonColor: string;
  buttonLabel: string;
  offer?: Price | null;
  recommended: boolean;
  darkBtn: boolean;
  bottomTagline?: string;
}
const plans: Array<Plans> = [
  {
    name: "Starter",
    price: {
      monthly: 0,
      annual: 0,
    },
    discount: null,
    features: [
      "Basic Themes",
      "2 Affiliate Links",
      "Limited Monetization Features",
    ],
    buttonColor: "#E5E7EB",
    buttonLabel: "Current Plan",
    offer: null,
    recommended: false,
    darkBtn: false,
  },
  {
    name: "Style",
    price: {
      monthly: 7,
      annual: 84,
    },

    cents: 99,
    discount: 20,
    features: [
      "Premium Themes",
      "2 Affiliate Links",
      "Limited Monetization Features",
      "Advanced Style Customization",
    ],
    buttonColor: "#4624D6",
    buttonLabel: "Choose Plan",
    offer: {
      monthly: 9.99,
      annual: 119.88,
    },
    recommended: false,
    darkBtn: true,
    bottomTagline: "When you just want a nicer page",
  },
  {
    name: "Pro",
    price: {
      monthly: 7,
      annual: 168,
    },
    cents: 99,
    discount: 25,
    features: [
      "Premium Themes",
      "Unlimited Affiliate Links",
      "Tons of Monetization Features",
      "Advanced Style Customization",
      "Media Kit",
      "Auto-Pull",
    ],
    buttonColor: "#4624D6",
    buttonLabel: "Choose Plan",
    offer: {
      monthly: 19.99,
      annual: 239.88,
    },
    recommended: true,
    darkBtn: true,
    bottomTagline: "Take it to the next level",
  },
];
export default defineComponent({
  components: { Switch, Chip },
  data: () => ({
    plans,
    annual: false,
  }),
  methods: {
    switchChanged(val: any) {
      this.annual = val;
    },
  },
});
</script>


<style lang="sass">
@import "../styles/paywall.sass"
</style>
<style>
.hide-scroll-bar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.hide-scroll-bar::-webkit-scrollbar {
  display: none;
}
</style>