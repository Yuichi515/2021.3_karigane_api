<template>
  <div id="app">
      <div class="home">
      <!-- 郵便番号を入力 addressNoに番号を入れる-->
      <input type="text" v-model="addressNo" />
      <!-- クリックすると住所を表示するボタン showを実行する-->
      <button @click="show">住所入力</button>
      <!-- 住所を表示 -->
      <p>Address:{{ yourAddress }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return {
      addressNo: '',
      yourAddress: ''
    }
  },
  methods: {
    show(){
      axios.get(
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.addressNo}/Key=PdnXtUYgN6UG5QyfyF8gB1jJhbPO7bXycVLbxD6`)
        .then(response => {
          // console.log(response)
          this.yourAddress = response.data.allAddress;
        })
    }
  }
}
</script>


<style>
</style>
