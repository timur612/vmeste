<template>
    <view class="container">
        <text class="heading">Тренировка</text>
        <view :style="{height:300,padding:10}">
            <web-view :style="{borderRadius:30}" :source="{uri:'https://www.youtube.com/embed/hj1_a7umGNI?rel=0&autoplay=0&showinfo=0&controls=0'}" />
        </view>
        <text class="text">Йога для начинающих</text>
        <view class="s-container">
                    <text class="card_text_p">15 мин</text>
                    <text  class="card_text_p">5 баллов</text>
                    <text  class="card_text_p" :style="{marginLeft:55}">Не выполнено</text>
        </view>
    </view>
    
</template>

<script>
import { WebView } from "react-native-webview";

export default {
  name: "myComponent",
  components: {
    "web-view": WebView
  }
};
</script>
<style scoped>
.text{
    font-size: 18;
    margin-top:24;
    margin-left:24;
}
.card_text_p{
    margin-left:25;
    margin-bottom:15;
}
.s-container{
    margin-top:10;
    /* flex:1; */
    flex-direction: row;
    flex-wrap: wrap;
}
.heading {
  font-size: 24;
  font-weight:500;
  color: black;
  margin-left: 10;
}
.container {
  flex: 1;
  padding: 10;
}
</style>