<template>
    <scroll-view class="container">
        <text class="heading">Сообщество</text>
        <view class="profile" :style="styles.shadowBox">
            <view class="self_zone">
                <image :source="require('../assets/avatar.png')"/>
                <view :style="{marginLeft:25}">
                    <text class="name">Иванов Иван</text>
                    <touchable-opacity class="btn"><text>Редактировать профиль</text></touchable-opacity>
                </view>
            </view>
            <view :style="{padding:10,flexDirection:'row'}">
                <text :style="{fontSize:16}">E-mail</text>
                <text :style="{fontSize:16,color:'#c4c4c4',marginLeft:130}">example@gmai.com</text>
            </view>
            <view :style="{padding:10,flexDirection:'row'}">
                <text :style="{fontSize:16}">Баллы</text>
                <text :style="{fontSize:16,color:'#c4c4c4',marginLeft:260}">5</text>
            </view>
        </view>

        <view class="raiting" :style="styles.shadowBox">
            <text class="heading">Рейтинг</text>
            <view class="centered">
                <view v-for="(part,index) in people" :key="index" :style="{flexDirection:'row'}">
                    <text :style="{fontSize:17}">{{index+1}}</text>
                    <text :style="{fontSize:17,marginLeft:15}">{{part.name}}</text>
                    <text :style="{fontSize:17,marginLeft:15}">{{part.score}}</text>
                </view>
            </view>
            
        </view>
    </scroll-view>
</template>

<script>
import { StyleSheet } from 'react-native';

const styles = new StyleSheet.create({
  shadowBox: {
    elevation: 20,
    shadowOffset: { width: 2, height: 2 },
    shadowColor: 'black',
    shadowOpacity: 0.2,
    height: 'auto',
    backgroundColor: 'white',
    shadowRadius: 5,
    borderRadius:15,
  },
});
export default {
    data:function(){
        return {
            styles,
            people:[
                {name:'Иванов Иван',score:120},
                {name:'Иванов Иван',score:101},
                {name:'Иванов Иван',score:99},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
                {name:'Иванов Иван',score:98},
            ]
        }
    }
}
</script>

<style scoped>
.container {
  flex: 1;
  padding: 10;
  /* flex-direction: row; */
}
.raiting{
    margin-top:25;
    padding:10;
   
}
.centered{
    align-content: center;
    align-items: center;

    margin-top: 20;
}
.profile{
    margin-top:15;
}
.heading{
  font-size: 24;
  font-weight:500;
  color: black;
  margin-left: 10;
}
.self_zone{
    flex-direction: row;
    padding:15;
}
.name{
    font-size:16;
    margin-top:10;
}
.btn{
    margin-top:5;
    background-color: #EDEDED;
    padding-left: 25;
    padding-right: 25;
    padding:6;
    border-radius: 5;
}
</style>
