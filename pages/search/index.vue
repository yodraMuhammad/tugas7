<template>
  <!-- Hero section -->
  <section id="home" class="pt-36 mb-20">
    <div class="container">
      <div class="flex justify-center items-center text-center ">
        <div class="w-full self-center px-4 lg:w-1/2 mb-10">
          <h1
            class="text-base font-semibold text-primary md:text-xl lg:text-2xl"
          >
            Cari Film
            <span
              class="block font-bold text-dark mb-2 text-4xl mt-1 lg:text-5xl"
              >Favorit Anda</span
            >
          </h1>
          <p class="font-medium text-secondary mb-10 leadinng-relaxed">
            Website pencarian film adalah sebuah platform online yang memungkinkan pengguna untuk mencari informasi tentang film-film yang ada. Website tersebut menyediakan berbagai fitur dan fungsi yang membantu pengguna untuk menemukan film-film yang mereka cari.
          </p>
        </div>
      </div>

        <div class="flex justify-end">
            <form class="flex items-center" @submit.prevent="handleSubmit">
              <input
                type="text"
                class="border border-gray-300 px-4 py-2 rounded-l-md focus:outline-none focus:ring focus:border-blue-300"
                placeholder="Cari..."
                v-model="input"
                @keyup.enter="cariFilm(input)"
              />
              <a
                class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-r-md ml-2"
                @click="cariFilm(input)"
              >
                Cari
              </a>
            </form>
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
          v-for="data in datas"
          :key="data.id"
        >
          <nuxt-link :to="'/search/detail/'+data.imdbID">
            <card
              class="card"
              :title="data.Title"
              :tahun="data.Year"
              :description="data.Type"
              :image="data.Poster"
              :id="'/search/detail/'+data.imdbID"
            />
          </nuxt-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      films: [],
      datas: {},
      input: "",
    };
  },
  methods: {
    setFilm(data) {
      this.films = data;
    },
    async cariFilm(input) {
      const { data: film } = await useFetch(
        "https://www.omdbapi.com/?apiKey=41243417&s=" + input
      );
      this.datas = film._rawValue.Search;
      console.log(film._rawValue.Search);
    },
  },
};
</script>

<script setup>
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
