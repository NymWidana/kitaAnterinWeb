<script setup>
import { ref } from "vue";
const navs = [
  {
    teks: "HOME",
    url: "/",
  },
  {
    teks: "SHOP",
    url: "/Shop",
  },
  {
    teks: "TIPS",
    url: "/Tips",
  },
];

function myFunction() {
  var element = document.getElementById("hamBtn");
  element.classList.toggle("close");
  var element = document.getElementById("nav");
  element.classList.toggle("open");
}

const products = [
  {
    name: "Sayur lokal / local vegies",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "vegetables",
    price: 12850,
  },
  {
    name: "buah lokal / local fruits",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "fruits",
    price: 12850,
  },
  {
    name: "daging lokal / local meats",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "meats",
    price: 12850,
  },
  {
    name: "obat lokal / local herbs",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "herbs",
    price: 12850,
  },
  {
    name: "seafood lokal / local seafoods",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "seafoods",
    price: 12850,
  },
  {
    name: "Wortel lokal / local carrot",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "others",
    price: 12850,
  },
  {
    name: "Sayur lokal / local vegies",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "vegetables",
    price: 12850,
  },
  {
    name: "buah lokal / local fruits",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "fruits",
    price: 12850,
  },
  {
    name: "daging lokal / local meats",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "meats",
    price: 12850,
  },
  {
    name: "obat lokal / local herbs",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "herbs",
    price: 12850,
  },
  {
    name: "seafood lokal / local seafoods",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "seafoods",
    price: 12850,
  },
  {
    name: "Wortel lokal / local carrot",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "others",
    price: 12850,
  },
  {
    name: "Sayur lokal / local vegies",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "vegetables",
    price: 12850,
  },
  {
    name: "Sayur lokal / local vegies",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "vegetables",
    price: 12850,
  },
  {
    name: "Sayur lokal / local vegies",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "vegetables",
    price: 12850,
  },
  {
    name: "Wortel lokal / local carrot",
    urlGambar:new URL( "./src/assets/wortel.png", import.meta.url).href,
    category: "others",
    price: 12850,
  },
];
const categories = [
  "All",
  "Vegetables",
  "Fruits",
  "Meats",
  "Herbs",
  "Seafoods",
  "Others",
];

const productsPerPage = ref(12);
const selectedCategory = ref("all");
const searchQuery = ref("");
const currentPage = ref(1);

function filteredProducts() {
  let filteredProducts = products;
  if (selectedCategory.value !== "all") {
    filteredProducts = filteredProducts.filter(
      (product) => product.category === selectedCategory.value
    );
  }
  if (searchQuery.value !== "") {
    filteredProducts = filteredProducts.filter((product) =>
      product.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  }
  return filteredProducts;
}
function totalPages() {
  return Math.ceil(filteredProducts().length / productsPerPage.value);
}
function paginatedProducts() {
  const startIndex = (currentPage.value - 1) * productsPerPage.value;
  return filteredProducts().slice(
    startIndex,
    startIndex + productsPerPage.value
  );
}
</script>

<template>
  <header class="bg-bannerp relative z-50">
    <nav class="border-gray-200 bg-black bg-opacity-50 backdrop-blur-sm">
      <div
        class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
      >
        <router-link to="/" class="flex items-center">
          <img
            src="../assets/kitaanterinlogo4.png"
            class="h-12 mr-3"
            alt="Kita Anterin Logo"
          />
        </router-link>
        <div class="flex items-center">
          <button
            id="hamBtn"
            type="button"
            class="text-sm rounded-sm md:hidden"
            @click="myFunction"
          >
            <span></span>
            <span></span>
            <span></span>
          </button>
        </div>
        <div id="nav" class="hidden md:block w-full md:w-auto">
          <ul
            class="flex flex-col font-medium m-4 rounded-lg bg-black bg-opacity-50 md:bg-opacity-0 backdrop-blur-sm md:backdrop-blur-none md:flex-row md:space-x-8 md:m-0 md:border-0 md:bg-transparent"
          >
            <li v-for="nav in navs">
              <router-link
                :to="nav.urlGambar"
                class="block py-2 pl-3 pr-4 text-white rounded md:bg-transparent md:p-0"
                >{{ nav.teks }}</router-link
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <!-- banner -->
  <div class="bg-bannerp h-banner flex items-center justify-center relative -z-50">
    <div
      class="text-3xl sm:text-5xl lg:text-6xl text-white bg-black bg-opacity-20 p-8 rounded-full fixed -translate-y-24"
    >
      OUR PRODUCTS
    </div>
  </div>

  <!-- content -->
  <div class="bg-white mx-auto max-w-screen-xl pt-8 md:pt-16">
    <div class="bg-greenka p-2 rounded-full mx-4 md:mx-8 mb-4 md:mb-8">
      <div
        class="ml-auto rounded-full py-2 px-4 w-48 sm:w-64 bg-white flex items-center gap-1"
      >
        <img src="../assets/searchicon.svg" class="w-5" alt="searchicon" />
        <input
          type="text"
          class="focus:outline-none w-full"
          placeholder="Search...."
          v-model="searchQuery"
        />
      </div>
    </div>
    <div class="mx-6 sm:mx-12 md:mx-24">
      <!-- category -->
      <div
        class="flex gap-2 md:gap-4 my-4 md:my-8 overflow-x-scroll md:overflow-x-auto text-sm sm:text-base"
      >
        <button
          class="categorybtn p-1 sm:p-2 px-4 sm:px-8 md:px-0 border-black border-2 cursor-pointer rounded-full grow text-center hover:bg-greenka2 hover:text-white hover:border-greenka2 transition"
          v-for="category in categories"
          @click="
            selectedCategory = category.toLowerCase();
            currentPage = 1;
          "
          :class="category"
        >
          {{ category }}
        </button>
      </div>
      <div
        class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-8 pb-8 md:pb-16"
      >
        <a
          href="#"
          class="rounded-3xl overflow-hidden flex flex-col p-4 gap-8 shadow-lg shadow-slate-400 hover:shadow transition"
          v-for="(product, index) in paginatedProducts()"
        >
          <img
            src="../assets/kitaanterinlogo.png"
            class="w-12 mx-auto"
            alt="logokitaanterin"
          />
          <div>
            <img
              :src="product.urlGambar"
              class="mx-auto"
              :alt="'gambar ' + product.name"
            />
          </div>
          <div>
            <div class="font-medium sm:text-xl">
              {{
                product.price.toLocaleString("id-ID", {
                  style: "currency",
                  currency: "IDR",
                })
              }}
            </div>
            <div class="text-sm sm:text-base">{{ product.name }}</div>
          </div>
        </a>
      </div>
      <div class="m-auto sm:ml-auto w-fit flex gap-4 sm:gap-8 pb-12 md:pb-24 items-center">
        <button
          @click="currentPage--"
          :disabled="currentPage === 1"
          class="text-white text-sm sm:text-base font-medium p-2 px-4 sm:px-8 bg-greenka3 rounded-xl"
        >
          &lt;pre
        </button>
        <div>{{ currentPage }}/{{ totalPages() }}</div>
        <button
          @click="currentPage++"
          :disabled="currentPage === totalPages()"
          class="text-white text-sm sm:text-base font-medium p-2 px-4 sm:px-8 bg-greenka3 rounded-xl"
        >
          next&gt;
        </button>
      </div>
    </div>
  </div>
</template>
<style>
.bg-bannerp {
  background: url(../assets/bannerp.png) center/cover no-repeat fixed;
}
</style>
