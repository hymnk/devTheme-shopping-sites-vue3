<script setup>
import { ref, computed } from 'vue'
import { items } from './items.js'

const price = ref(0)
const theme = ref('light')
const drawer = ref(false)

const selectedItems = ref({})

const addToTotal = (item) => {
  selectedItems.value[item.id] = !selectedItems.value[item.id]

  if (selectedItems.value[item.id]) {
    price.value += item.price
  } else {
    price.value -= item.price
  }
}

function formatPrice(price) {
  return price.toLocaleString()
}

const formattedPrice = computed(() => {
  return price.value.toLocaleString()
})

const themeOnClick = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
  <v-app :theme="theme">
    <v-app-bar color="primary">
      <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer" />
      <v-app-bar-title>架空バードショップ</v-app-bar-title>
      <v-btn
        :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
        text="Toggle Theme"
        slim
        @click="themeOnClick"
      />
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" temporary>
      <v-list>
        <v-list-item title="111"></v-list-item>
        <v-list-item title="222"></v-list-item>
        <v-list-item title="333"></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main style="width: 100%; height: 100%">
      <v-container>
        <v-row justify="center">
          <v-col cols="6">
            <div class="text-h2 pa-2">商品一覧</div>
          </v-col>
          <v-col cols="6" :style="{ textAlign: 'right' }">
            <div class="text-h2 pa-2">合計金額: {{ formattedPrice }}円</div>
          </v-col>

          <v-divider />

          <v-col v-for="item in items" :key="item.id" cols="4">
            <v-card :color="selectedItems[item.id] ? 'primary' : ''" @click="addToTotal(item)">
              <v-card-title class="text-h3">{{ item.name }}</v-card-title>
              <!-- TODO 算出プロパティでカンマつけたほうがいいかもしれない -->
              <v-card-text class="text-h4">{{ formatPrice(item.price) }} 円</v-card-text>
              <v-card-text v-if="item.description">Prompt: {{ item.description }}</v-card-text>
              <div class="image-container">
                <img :src="item.image" alt="Image" />
              </div>
            </v-card>
          </v-col>

          <v-divider />
        </v-row>
      </v-container>
    </v-main>

    <v-footer class="bg-secondary" app>
      <div class="py-3 text-center w-100">
        <span>&copy; {{ new Date().getFullYear() }} Footer Area.</span>
      </div>
    </v-footer>
  </v-app>
</template>

<style>
.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}
.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
