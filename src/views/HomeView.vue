<script setup></script>

<template>
  <main>test</main>
  <router-link :to="{ name: 'modal', params: { id: 1 } }">Open Modal</router-link>
  <router-view></router-view>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Nobis dignissimos tempore a, quod porro
    voluptates eligendi laudantium voluptas, officia aliquid quibusdam omnis asperiores veritatis,
    doloremque rerum minus corrupti exercitationem iure!
  </p>
</template>
