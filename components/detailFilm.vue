<script setup>

const route = useRoute();
const { data: film } = await useFetch(
  "https://www.omdbapi.com/?apiKey=41243417&i=" + route.params.id
);

const { data } = await useAsyncData('count', () => $fetch("https://www.omdbapi.com/?apiKey=41243417&i=" + route.params.id))
console.log(data._rawValue)
</script>

<template>
  <section id="detail" class="pt-36 mb-20">
    <div class="container">
      <div class="flex">
        <div class="md:w-1/3">
          <img :src="film.Poster" alt="" />
        </div>
        <div class="md:w-2/3">
          <h1 class="text-4xl mb-6">{{ film.Title }}</h1>
          <table class="border-collapse">
            <tbody>
              <tr>
                <td class="p-2 align-top">Rilis</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Year }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Rating</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.imdbRating }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Genre</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Genre }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Director</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Director }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Actors</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Actors }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Writer</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Writer }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Language</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Language }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Country</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Country }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Plot</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ film.Plot }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </section>
</template>


