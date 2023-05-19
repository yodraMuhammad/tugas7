<template>
    <div class="my-component">
      <div class="max-w-sm rounded overflow-hidden shadow-lg">
        <img class="w-full gambar" :src="image"  />
        <div class="px-6 py-4">
          <!-- Title -->
          <div class="font-bold text-xl mb-2">{{ title }}</div>
  
          <!-- Star -->
          <div class="flex items-center mt-2.5 mb-4">
            <span>{{ description }}</span>
            <span
              class="bg-blue-100 text-blue-800 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded dark:bg-blue-200 dark:text-blue-800 ml-3">{{ tahun }}</span>
          </div>

          <!-- Button -->
          <div class="py-6">
            <nuxt-link :to="id" class="w-1/4 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full mb-4">See Detail</nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "card",
    data() {
      return {
        star_number: 0
      }
    },
    props: {
      title: {
        type: String,
        required: true,
      },
      description: {
        type: String,
        required: true,
      },
      image: {
        type: String,
        required: true,
      },
      tahun: {
        type: String,
        required: true,
      },
      id: {
        type: String,
        required: true,
      },
    },
    methods: {
      formatNumber(num) {
        return num.toFixed(1);
      }
    },
    mounted() {
      this.star_number = this.star;
    }
  };
  </script>
  
  <style scoped></style>
  