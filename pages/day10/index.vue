<template>
    <!-- Hero section -->
    <section id="home" class="pt-36 mb-10">
        <div class="container">
            <div class="flex justify-center items-center text-center">
                <div class="w-full self-center px-4 lg:w-1/2 mb-10">
                    <h1 class="text-base font-semibold text-primary md:text-xl lg:text-2xl">
                        Day 10
                        <span class="block font-bold text-dark mb-2 text-4xl mt-1 lg:text-5xl">Membuat Function</span>
                    </h1>
                </div>
            </div>
        </div>
    </section>
    <!-- Hero section end -->

    <!-- card -->
    <section id="card" class="mb-30 pb-35 text-center">
        <div class="container">
            <hr class="mb-10" />
            <div class="mb-10">
                <h1 class="text-base mb-3 font-semibold text-primary md:text-xl lg:text-2xl">Soal 1</h1>
                    <input type="text"
                        class="border border-gray-300 px-4 py-2 rounded-l-md focus:outline-none focus:ring focus:border-blue-300"
                        placeholder="Masukan Text" v-model="input" @keyup.enter="ubahString(input)" />
                    <button class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-r-md ml-1"
                        @click="ubahString(input)">
                        Submit
                    </button>
                    <button
                    class="flex-shrink-0 border-transparent border-4 text-red-500 hover:text-red-800 text-sm py-1 px-2 rounded"
                    type="button" @click="reset2()">
                    Reset
                </button>
                <p class="text-xl font-semibold mt-3">Hasil : {{ output }}</p>
            </div>
            <hr class="mb-10" />
            <div class="mb-10">
                <h1 class="text-base text-center mb-3 font-semibold text-primary md:text-xl lg:text-2xl">Soal 2</h1>
                <div class="text-center mb-3">
                    <p class="text-md font-semibold">Sebelum</p>
                    <div class="flex justify-center">
                        <table class="md:w-1/2 sm:w-1/1 text-sm text-left text-gray-500 dark:text-gray-400">
                            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        Name</th>
                                    <th scope="col" class="px-6 py-3">
                                        Age</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700"
                                    v-for="data in inputArray" :key="data.id">
                                    <td class="border px-4 py-2">{{ data.name }}</td>
                                    <td class="border px-4 py-2">{{ data.age }}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                <div class="text-center">
                    <p class="text-md font-semibold">Sesudah</p>
                    <div class="flex justify-center">
                        <table class="md:w-1/2 sm:w-1/1 text-sm text-left text-gray-500 dark:text-gray-400">
                            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        Name</th>
                                    <th scope="col" class="px-6 py-3">
                                        Age</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700"
                                    v-for="data in getUniqueSortedObjects(inputArray)" :key="data.id">
                                    <td class="border px-4 py-2">{{ data.name }}</td>
                                    <td class="border px-4 py-2">{{ data.age }}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            <hr class="mb-10" />
            <div class="mb-10">
                <h1 class="text-base text-center mb-3 font-semibold text-primary md:text-xl lg:text-2xl">Soal 3</h1>
                <input type="text"
                    class="border border-gray-300 px-4 py-2 rounded-l-md focus:outline-none focus:ring focus:border-blue-300"
                    placeholder="Masukan Angka" v-model="input2" @keyup.enter="getRunningSum(input2)"
                    @keyup="handleInputChange" 
                    @keyup.backspace="hapus()" />
                <button class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-r-md ml-1"
                    @click="getRunningSum(input2)">
                    Submit
                </button>
                <button
                    class="flex-shrink-0 border-transparent border-4 text-red-500 hover:text-red-800 text-sm py-1 px-2 rounded"
                    type="button" @click="reset()">
                    Reset
                </button>
                <p class="text-xl font-semibold mt-3">hasil :{{ output2 }}</p>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            input: '',
            input2: '',
            output: '',
            output2: [],
            inputArray: [
                { name: "John", age: 25 },
                { name: "Jane", age: 30 },
                { name: "John", age: 35 },
                { name: "Alice", age: 28 }
            ],
        };
    },
    methods: {
        ubahString(data) {
            const words = data.split(" ");

            const mergedString = words.map((word) => word.split("").join("@")).join(" ");
            console.log(typeof mergedString);
            this.output = mergedString;
        },
        getUniqueSortedObjects: (array) => {
            const uniqueNames = new Set();
            const uniqueObjects = [];

            array.forEach((obj) => {
                if (!uniqueNames.has(obj.name)) {
                    uniqueNames.add(obj.name);
                    uniqueObjects.push(obj);
                }
            });
            uniqueObjects.sort((a, b) => a.name.localeCompare(b.name));
            return uniqueObjects;
        },
        handleInputChange() {
            const lastChar = this.input2.slice(-1);
            if (/^[0-9]$/.test(lastChar)) {
                this.input2 += ",";
            }
        },
        getRunningSum(input) {
            let sum = 0;
            input = input.slice(0, -1);
            const arr = input.split(",").map(Number);

            const outputArray = arr.map((num) => {
                sum += num;
                return sum;
            });
            this.output2 = outputArray;
        },
        reset() {
            this.input2 = '';
            this.output2 = '';
        },
        reset2() {
            this.input = '';
            this.output = '';
        },
        hapus(){
            if (this.input2.length >= 2) {
                const newValue = this.input2.slice(0, -2);
                this.input2 = newValue;
            }
        },
    }
}

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