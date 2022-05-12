<script setup>
  import image from "../assets/Mega Man Zero 2.png"
  import {ref} from 'vue'

  const selected = ref(null)
  const sidebarList = [
    {icon: 'box-archive', name: "Products"},
    {icon: 'copy', name: "Whitelists"},
    {icon: 'shuffle', name: "Api Application"}
  ]
  const productList = [
    {size: "-11px -12px"},
    {size: "-272px -12px"},
    {size: "-540px -12px"},
    {size: "-805px -12px"},
    {size: "-1072px -12px"},
    {size: "-12px -193px"},
    {size: "-273px -193px"},
    {size: "-540px -193px"},
    {size: "-806px -193px"},
    {size: "-1072px -193px"},
    {size: "-13px -375px"},
    {size: "-274px -375px"},
    {size: "-540px -375px"},
    {size: "-806px -375px"},
    {size: "-1072px -375px"},
  ]
</script>

<template>
  <section class="flex w-screen h-screen">
    <div class="w-72 sidebar">
      <div class="sidebar-logo">
        Westeros
      </div>
      <div class="sidebar-item" v-for="item in sidebarList" :key="item">
        <font-awesome-icon :icon="item.icon" /> 
        <span class="px-4">{{item.name}}</span>
      </div>
    </div>
    <div class="flex-1 bg-white overflow-auto">
      <header class="header">
        <div class="input-icons">
          <input class="input-field" 
                    type="text"
                    placeholder="Type to search ...">
          <font-awesome-icon icon="magnifying-glass" /> 
        </div>
        <!-- <input type="text" placeholder="Type to search"> -->
        <div class="text-gray-500 cursor-pointer">
          <font-awesome-icon icon="circle-user" size="2xl"/> 
          <span class="px-4">Lorum ipsum</span>
        </div>
      </header>
      <main class="p-8 space-y-4">
        <h2 class="px-4 text-3xl text-gray-400">Products</h2>
        <hr class="mx-4"/>
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5" v-if="selected === null">
          <div class="card" v-for="(product, key) in productList" :key="product" @click="selected = key">
            <!-- <figure style="background: url('@/assets/Mega Man Zero 2.png') no-repeat -1072px -193px;"></figure> -->
            <img :src="image" alt="product" :style="`object-position: ${product.size}; object-fit: none; width: 240px; height:160px`">
            <!-- <img :src="`https://picsum.photos/200?random=${i}`" alt="Avatar" style="width:100%"> -->
            <div class="py-4">
              <h4><b>Lorum ipsum</b></h4>
              <p>by random author</p>
            </div>
          </div>
        </div>

        <div class="space-y-4 px-4" v-if="selected || selected === 0">
          <button class="text-gray-500 text-xl" @click="selected = null">
            <font-awesome-icon icon="circle-left" size="xl"/> 
            Back
          </button>
          <img :src="image" alt="product" :style="`object-position: ${productList[selected].size}; object-fit: none; width: 240px; height:160px`">
          <div class="space-y-4 py-4">
            <div>
              <h2 class="text-2xl"><b>Lorum ipsum</b></h2>
              <p>by random author</p>
            </div>
            <p>Description</p>
            <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. 
              Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
              when an unknown printer took a galley of type and scrambled it to make a type specimen book. 
              It has survived not only five centuries, but also the leap into electronic typesetting, 
              remaining essentially unchanged. It was popularised in the 1960s with the release of 
              Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing 
              software like Aldus PageMaker including versions of Lorem Ipsum.
              </p>
          </div>
        </div>
      </main>
    </div>
  </section>
</template>

<style>
@import url('http://fonts.cdnfonts.com/css/calibri-light');
@import url('https://fonts.googleapis.com/css2?family=Arvo:wght@700&display=swap');

section {
  font-family: 'Calibri Light', sans-serif;
}

.sidebar {
  background-color: #3f4044;
  color: #fff;
  height: 100vh;
}

.sidebar-logo {
  font-family: 'Arvo', serif;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #047ce6;
  color: #fff;
  font-size: 28px;
  height: 80px;
}

.sidebar-item {
  @apply px-8 transition duration-300;
  display: flex;
  align-items: center;
  height: 60px;
}
.sidebar-item:hover {
  background-color: #5f5f5f;
  cursor: pointer;
}

.header {
  @apply px-8;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f4f3f3;
  height: 80px;
}

.card {
  @apply p-4 transition duration-300;
}
.card:hover {
  transform: scale(1.05);
  background-color: #ddd;
}

.input-icons i {
    position: absolute;
}
  
.input-icons {
  padding-left: 20px;
  padding-right: 20px;
  display: flex;
  align-items: center;
  background-color: #fff;
  border-radius: 20px;
  height: 40px;
}
  
.input-field {
  outline: none;
  padding-right: 10px;
}
</style>