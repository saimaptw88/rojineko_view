re
<template>
  <div>
    <div class="box" v-for="cat in cats" :key="cat.url">
      <img class="image" :src="cat.url" />
      <div>Adress : {{ cat.address }}</div>
      <div>CreateDate : {{ cat.createDate }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cats: [],
    }
  },
  async created() {
    try {
      const response = await this.$axios
        .get('https://jsondata.okiba.me/v1/json/7lV2J201227155106')
        .then((response) => {
          this.cats = response.data.results
        })
      console.log(response)
    } catch (err) {
      const res = err.response
      console.log(res)
    }
  },
  mounted() {
    console.log('mounted')
  },
}
</script>

<style lang="scss">
.box {
  border-bottom: 1px solid gray;
  padding: 10px;
  margin: 40px;
  .image {
    max-width: 400px;
    min-width: 300px;
    max-height: 400px;
    min-height: 300px;
  }
}
</style>
