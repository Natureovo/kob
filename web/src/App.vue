<template>
  <div>
    <div>Bot昵称：{{bot_name}}</div>
    <div>Bot战力：{{bot_rating}}</div>
  </div>
  <router-view/>
</template>

<script>
import $ from 'jquery'
import {ref} from 'vue';

export default {
  name:"App",
  setup:() => {
    let bot_name = ref("");
    let bot_rating = ref("");

    $.ajax({
      url: "http://localhost:3000/pk/getbotinfo/",
      type: "get",
      success: resp => {
        bot_name.value = resp.name;
        bot_rating.value = resp.rating;
      }
    });

    return {
      bot_name,
      bot_rating
    }

  }
}
</script>

<style>
body {
  /* @表示根目录,因为版本问题前面要加~ 
  问题链接：https://blog.csdn.net/wangdong9395/article/details/106042047/
  */
  background-image: url("~@/assets/background.png");
  background-size: cover;
}
</style>
