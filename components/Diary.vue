<template>
    <view class="container">
        <text class="heading">Дневник питания</text>
        <view class="main">
            <view >
                <view class="bar">
                <view class="bar_main">
                    <view class="bar_color" :style="{width:wBelki,backgroundColor:'#0085ff'}"></view>
                </view>
                    <!-- <text class="bar-text">Выполнено тренировок: 1 из 3</text> -->
                </view>
                <view class="bar">
                <view class="bar_main">
                    <view class="bar_color" :style="{width:wZir,backgroundColor:'#5FD043'}"></view>
                </view>
                    <!-- <text class="bar-text">Выполнено тренировок: 1 из 3</text> -->
                </view>
                <view class="bar">
                <view class="bar_main">
                    <view class="bar_color" :style="{width:wUgle,backgroundColor:'#FFD500'}"></view>
                </view>
                    <!-- <text class="bar-text">Выполнено тренировок: 1 из 3</text> -->
                </view>
            </view>
            <view class="texts">
                <text class="prog_text">Белки <text :style="{color:'#c4c4c4'}">17 г</text></text>
                <text class="prog_text">Жиры <text :style="{color:'#c4c4c4'}">110 г</text></text>
                <text class="prog_text">Углеводы <text :style="{color:'#c4c4c4'}">39 г</text></text>
            </view>
        </view>
        <view class="add_list">
            <text class="heading">Сегодня</text>
            <view class="choose">
               <image
                        :style="{height:70,width:70}"
                        :source="require('../assets/breakfast.png')"
                    />
                <view :style="{margin:17}">
                    <text class="main">Завтрак</text>
                    <text class="p">Рекомендуется 336-551 ккал</text>
                </view>
                <touchable-opacity :on-press="addToTotal" class="btn">
                    <text :style="{fontSize:17}">+</text>
                </touchable-opacity>
            </view>
            <view class="choose">
               <image
                        :style="{height:55,width:70}"
                        :source="require('../assets/soup.png')"
                    />
                <view :style="{margin:17}">
                    <text class="main">Обед</text>
                    <text class="p">Рекомендуется 551-734 ккал</text>
                </view>
                <touchable-opacity :on-press="addToTotal" class="btn">
                    <text :style="{fontSize:17}">+</text>
                </touchable-opacity>
            </view>
            <view class="choose">
               <image
                        :style="{height:70,width:70}"
                        :source="require('../assets/dinner.png')"
                    />
                <view :style="{margin:17}">
                    <text class="main">Ужин</text>
                    <text class="p">Рекомендуется 551-734 ккал</text>
                </view>
                <touchable-opacity :on-press="addToTotal" class="btn">
                    <text :style="{fontSize:17}">+</text>
                </touchable-opacity>
            </view>
            <view class="Total">
                <text>Всего ккал {{total}}</text>
            </view>
        </view>
    </view>
</template>

<script>
import Vue from 'vue-native-core'
import {CircularProgressbar} from 'react-circular-progressbar'

Vue.component('prog-circle', CircularProgressbar)
export default {
    data:function(){
        return {
            total: 0,
            wBelki: 0,
            wZir: 0,
            wUgle: 0
        }
    },
    methods:{
        addToTotal(){
            this.total+=Math.round(Math.random()*300)
            
            if(this.wBelki<200){
                this.wBelki+=Math.round(Math.random()*50)
            }
            if(this.wZir<200){
                this.wZir+=Math.round(Math.random()*50)
            }
            if(this.wUgle<200){
                this.wUgle+=Math.round(Math.random()*50)
            }
            
        }
    },
    components:{CircularProgressbar}
}
</script>

<style>
.container {
  flex: 1;
  padding: 10;
  /* flex-direction: row; */
}
.main{
    font-size: 16;
}
.btn{
    height: 40;
    width: 40;
    align-items: center;
    padding-top: 7;
    border-radius: 100;
    background-color: #EDEDED;
}
.p{
    font-size: 14;
}
.choose{
    flex-direction: row;
    margin-top: 10;
}
.add_list{
    align-items: center;
    margin-top:15;
}
.heading {
  font-size: 24;
  font-weight:500;
  color: black;
  margin-left: 10;
}
.prog_text{
    font-size: 16;
    margin-top:10;
}
.texts{
    margin:10;
}
.main{
    flex-direction: row;
}
.bar{
    width: auto;
    margin-top:20;
}
.bar-text{
    font-size: 17;
    color: #c4c4c4;;
    /* font-weight: bold; */
}
.bar_main{
    width: 200;
    height: 15;
    background-color: #EDEDED;
    border-radius: 30;
}
.bar_color{
    
    height: 15;
    
    border-radius: 30;
}
</style>
