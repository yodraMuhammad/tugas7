<template>
    <!-- Hero section -->
    <section id="home" class="pt-36 mb-20">
      <div class="container">
        <div class="flex justify-center items-center text-center ">
          <div class="w-full self-center px-4 lg:w-1/2 mb-10">
            <h1
              class="text-base font-semibold text-primary md:text-xl lg:text-2xl"
            >
              Tugas 7
              <span
                class="block font-bold text-dark mb-2 text-4xl mt-1 lg:text-5xl"
                >Mebuat Json</span
              >
            </h1>
            <p class="font-medium text-secondary mb-4 mt-10 leadinng-relaxed">
              Const phi = {{ phi }}
            </p>
            <label for="" class="mb-3">Masukan jari-jari:</label><br>
            <input class="border border-gray-400" type="number" v-model="jari" placeholder="Inputkan Jari-jari">
            <br>
            <button @click="hitung(jari)" class="mt-4 ml-3 w-1/6 bg-red-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full">Hitung</button>
            <p v-show="hasil">Luas Lingkaran <span>{{hasil}}</span></p>
            <p v-show="hasil">Keliling Lingkaran <span>{{keliling}}</span></p>
            <br>
            <br>
            <a href="/db.json" class=" mt-10 w-1/4 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full">
                    File JSON
            </a>
          </div>
        </div>
      </div>
    </section>
    <!-- Hero section end -->
  
    <!-- card -->
    <section id="card" class="mb-30 pb-35">
      <div class="container">
        <hr class="mb-10">
        <div class="flex flex-wrap">
          <div
            class="w-full px-4 lg:w-1/4 md:w-1/2 sm:w-1/1 mb-10"
            v-for="data in datas.products"
            :key="data.id"
          >
            <nuxt-link :to="'/tugas/detail/'+data.id">
              <card
                class="card"
                :title="data.nama"
                :tahun="data.detail.rating"
                :description="'Rp '+data.harga"
                :image="data.image"
                :id="'/tugas/detail/'+data.id"
              />
            </nuxt-link>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import card from "~/components/card.vue";
  
  export default {
    components: {
      card,
    },
    data() {
      return {
        phi: 3.14,
        hasil: '',
        keliling: 0,
        datas: {
  "products": [
    {
      "id": 1,
      "nama": "Asus A4",
      "deskriksi": "Rilis Tahun 2018",
      "stok": 10,
      "harga": 14000,
      "discont": 0.1,
      "image": "https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full//85/MTA-2143560/asus_asus-x441ba-ga602t--amd-a6-9220-4gb-1tb-radeon-r4-w10-silver-14inch_full03.jpg",
      "detail": {
        "komentars": [
          {
            "nama": "Akbar",
            "komentar": "Produk sangat bagus",
            "tanggal": "2023-05-19"
          },
          {
            "nama": "Rizky",
            "komentar": "Produk kurang bagus",
            "tanggal": "2023-05-25"
          }
        ],
        "rating": 5.0,
        "terjual": 20
      }
    },
    {
      "id": 2,
      "nama": "Iphone 12",
      "deskriksi": "Rilis Tahun 2018",
      "stok": 10,
      "harga": 14000,
      "discont": 0.1,
      "image": "https://cdn.eraspace.com/media/catalog/product/i/p/iphone_12_pro_pacific_blue_1_3.jpg",
      "detail": {
        "komentars": [
          {
            "nama": "Akbar",
            "komentar": "Produk sangat bagus",
            "tanggal": "2022-05-19"
          }
        ],
        "rating": 5.0,
        "terjual": 20
      }
    }
  ]
},      
};
    },
    methods: {
      async cariFilm(input) {
        const { data: film } = await useFetch(
          "https://www.omdbapi.com/?apiKey=41243417&s=" + input
        );
        this.datas = film._rawValue.Search;
        console.log(film._rawValue.Search);
      },
      hitung(jari){
        this.hasil = this.phi*jari*jari
        this.keliling = 2*this.phi*jari
        console.log(this.hasil)
      }
    },
  };
  </script>
  
  <script setup>
  
  definePageMeta({
    layouts: "default",
  });
  
  onMounted(() => {
  
    const hamburger = document.querySelector("#hamburger");
    const navMenu = document.querySelector("#nav-menu");
  
    hamburger.addEventListener("click", function () {
      hamburger.classList.toggle("hamburger-active");
      navMenu.classList.toggle("hidden");
    });
  
    var counterContainer = document.querySelector("#website-counter");
    var visitCount = localStorage.getItem("page_view");
  
    if (visitCount) {
      visitCount = Number(visitCount) + 1;
      localStorage.setItem("page_view", visitCount);
    } else {
      visitCount = 1;
      localStorage.setItem("page_view", 1);
    }
    counterContainer.innerHTML = visitCount;
  });
  
  </script>
  