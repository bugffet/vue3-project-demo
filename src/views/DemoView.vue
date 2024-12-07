<template>
  <div class="demo">
    <h1>This is an demo page</h1>
    <div>
      <div v-for="{ name, img } in data.rows" :key="name">
        <h3>{{ name }}</h3>
        <img :src="img">
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, onMounted } from 'vue';
import axios from 'axios';

export default {
  setup() {
    const data = reactive({
      rows: '',
    })
    onMounted(() => {
      axios.get('/myapi/base64/W3sibmFtZSI6ImRlbW8iLCAiaW1nIjogIi9teWFwaS9pbWcvNjAweDQwMC9GRkZGRkYvMDAwMDAwL3BuZyJ9XQ==')
        .then((res) => {
          data.rows = res.data
        })
    });
    return { data };
  },
}
</script>

<style>
@media (min-width: 1024px) {
  .demo {
    min-height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;
  }
}
</style>
