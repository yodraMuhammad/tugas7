<template>
    <div id="home" class="">
        <div class="container mt-30 mt-44 mb-44">
            <div class="flex flex-wrap mt-30 mb-30">
                <div class="w-full self-center px-4 lg:w-1/2 md:w-1/2 sm:w-1/1 mb-10">
                    <h1 class="text-6xl mb-4 font-bold">Pencarian Film</h1>
                    <h2 class="text-2xl mb-4">Cari Film Kesukaan Anda</h2>
                    <nuxt-link to="/search"
                        class="w-1/2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-6 rounded-full">
                        Cari Film
                    </nuxt-link>
                </div>
                <div class="w-full px-4 lg:w-1/2 md:w-1/2 sm:w-1/1 mb-10">
                    <div class="flex justify-center items-center">
                        <img src="~/assets/images/frame1.png" alt="" width="500">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
