<script setup>
const route = useRoute();
const products = [
  {
    id: 1,
    nama: "Asus Vivabook 14",
    deskriksi: "Untuk kebutuhan bekerja atau bermain, ASUS VivoBook 14 M415 adalah laptop level entri yang memberikan kinerja bertenaga dan visual yang imersif. Layar NanoEdge-nya menawarkan sudut pandang 178° yang luas dan lapisan anti-glare untuk pengalaman yang benar-benar menarik. Di dalamnya, ditenagai oleh prosesor hingga AMD Athlon™ Gold 3150U dengan RAM 4GB. Desain penyimpanan dengan pilihan SSD PCIe® hinggai 512GB memberi Anda kecepatan baca/tulis data yang cepat.",
    stok: 10,
    harga: 2900000,
    discont: 0.1,
    image:
      "https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full//85/MTA-2143560/asus_asus-x441ba-ga602t--amd-a6-9220-4gb-1tb-radeon-r4-w10-silver-14inch_full03.jpg",
    detail: {
      komentars: [
        {
          nama: "Akbar Ferdianshah",
          komentar: "Produk sangat bagus",
          tanggal: "2023-05-19",
        },
        {
          nama: "Rizky Billar",
          komentar: "Produk kurang bagus",
          tanggal: "2023-05-25",
        },
      ],
      rating: 5.0,
      terjual: 20,
    },
  },
  {
    id: 2,
    nama: "Iphone 12",
    deskriksi: "iPhone 12. Layar Super Retina XDR 6,1 inci yang begitu cerah.1 Ceramic Shield dengan ketahanan jatuh empat kali lebih baik.2 Fotografi pencahayaan rendah yang menakjubkan dengan mode Malam di semua kamera. Mampu merekam, mengedit, dan memutar video sekelas sinema dengan Dolby Vision. Chip A14 Bionic yang andal. Dan aksesori MagSafe baru untuk kemudahan pemasangan dan pengisian daya nirkabel yang lebih cepat.3 Saatnya bersenang-senang.",
    stok: 10,
    harga: 2900000,
    discont: 0.1,
    image:
      "https://cdn.eraspace.com/media/catalog/product/i/p/iphone_12_pro_pacific_blue_1_3.jpg",
    detail: {
      komentars: [
        {
          nama: "M Akbar Bastian",
          komentar: "Produk sangat bagus",
          tanggal: "2022-05-19",
        },
      ],
      rating: 5.0,
      terjual: 20,
    },
  },
];

const product = products[route.params.id - 1];
</script>

<template>
  <section id="detail" class="pt-36 mb-20">
    <div class="container">
      <div class="flex">
        <div class="md:w-1/3">
          <img :src="product.image" alt="" />
        </div>
        <div class="md:w-2/3">
          <h1 class="text-4xl mb-6">{{ product.nama }}</h1>
          <table class="border-collapse">
            <tbody>
              <tr>
                <td class="p-2 align-top">Harga</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top" v-if="product.discont">
                  <del>Rp. {{ product.harga.toLocaleString() }}</del>
                  <strong> 
                    Rp. {{ (product.harga - (product.harga * product.discont)).toLocaleString() }} 
                  </strong>
                  <span class="bg-red-100 text-red-800 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded dark:bg-red-200
                    dark:text-red-800 ml-3">
                    - {{ Math.round(product.discont * 100) + '%' }}
                  </span>
                  </td>
                <td class="p-2 align-top" v-else>Rp. {{ product.harga.toLocaleString() }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Rating</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ product.detail.rating }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Stok</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ product.stok }} pcs</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Terjual</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ product.detail.terjual }} pcs</td>
              </tr>
              <tr>
                <td class="p-2 align-top">Deskripsi</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top">{{ product.deskriksi }}</td>
              </tr>
              <tr>
                <td class="p-2 align-top">komentar</td>
                <td class="p-2 align-top">:</td>
                <td class="p-2 align-top"></td>
              </tr>
            </tbody>
          </table>
          <div class="mt-3" v-for="data in product.detail.komentars" :key="data.id">
            <div class="border rounded-xl border-gray-400 p-4 flex flex-col justify-between leading-normal">

              <div class="flex items-center">
                <img class="w-10 h-10 rounded-full mr-4" src="https://v1.tailwindcss.com/img/jonathan.jpg"
                  alt="Avatar of Jonathan Reinink" />
                <div class="text-sm">
                  <p class="text-gray-900 leading-none">{{ data.nama }}</p>
                  <p class="text-gray-600">{{ data.tanggal }}</p>
                </div>
              </div>
              <div class="mb-8 mt-4">
                <p class="text-gray-700 text-base">
                  {{ data.komentar }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
