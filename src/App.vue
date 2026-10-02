<script setup>
import ProductList from "./components/ProductList.vue";
import { ref } from "vue";

const items = ref([
  {
    id: 1,
    title: "Apple Watch Series 7 синий",
    price: 34990,
    imageUrl: "/products/product-1.png",
  },
  {
    id: 2,
    title: "Beats Studio3 Wireless черный",
    price: 25000,
    imageUrl: "/products/product-2.png",
  },
  {
    id: 3,
    title: "Sony PlayStation 4 Slim черный",
    price: 30000,
    imageUrl: "/products/product-3.png",
  },
  {
    id: 4,
    title: "Apple iPhone 14 Pro 256 ГБ фиолетовый",
    price: 89990,
    imageUrl: "/products/product-4.png",
  },
  {
    id: 5,
    title: "Apple iPad Pro темно-серый",
    price: 114099,
    imageUrl: "/products/product-5.png",
  },
  {
    id: 6,
    title: "Чехол Apple iPhone 14 Pro Max оранжевый",
    price: 3400,
    imageUrl: "/products/product-6.png",
  },
  {
    id: 7,
    title: "Apple MacBook Air 13 серый",
    price: 119990,
    imageUrl: "/products/product-7.png",
  },
  {
    id: 8,
    title: "JBL Charge 5 черный",
    price: 15000,
    imageUrl: "/products/product-8.png",
  },
]);
</script>

<template>
  <body class="flex flex-col justify-between h-dvh">
    <div class="mx-auto w-[1440px] mb-25">
      <nav class="py-3 border-b border-b-slate-200">
        <div class="flex items-center justify-between">
          <div class="flex items-center gap-3">
            <img src="/logo.svg" alt="" />

            <p class="text-sm">
              Лучшие цены <br />
              в интернет-магазинах
            </p>
          </div>

          <ul class="flex gap-10">
            <li>
              <a href="" class="flex gap-3 items-center">
                <span class="p-3.5 rounded-xl bg-slate-100 hover:bg-slate-200 transition">
                  <img src="/cart-icon.svg" alt="" />
                </span>
                Корзина
              </a>
            </li>

            <li>
              <a href="" class="flex gap-3 items-center">
                <span class="p-3.5 rounded-xl bg-slate-100 hover:bg-slate-200 transition">
                  <img src="/like-outline.svg" alt="" />
                </span>
                Избранное
              </a>
            </li>

            <li>
              <a href="" class="flex gap-3 items-center">
                <span class="p-3.5 rounded-xl bg-slate-100 hover:bg-slate-200 transition">
                  <img src="/orders-icon.svg" alt="" />
                </span>
                Заказы
              </a>
            </li>
          </ul>
        </div>
      </nav>

      <main class="pt-10">
        <h1 class="text-[40px] font-bold mb-5">Каталог</h1>
        <product-list :items="items"></product-list>
      </main>
    </div>

    <footer class="p-6 bg-slate-100">
      <div class="text-center text-slate-500">
        Copyright © 2023 Behoof, Inc. Все права защищены
      </div>
    </footer>
  </body>
</template>

<style scoped></style>