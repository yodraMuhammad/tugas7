<script setup>

const route = useRoute();
</script>

<template>
  <suspense>
    <template #default>
        <DetailFilm :uid="route.params.id" />
        <!-- Tampilkan tampilan yang sesuai saat data dimuat -->
      </template>
      <template #fallback>
        <!-- <DetailFilm :uid="route.params.id" /> -->
        <!-- Tampilkan tampilan yang sesuai saat data selesai dimuat -->
        <DetailFilmLoad/>
      </template>
    </suspense>
</template>


