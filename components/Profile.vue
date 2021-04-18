<template>
    <scroll-view class="container">
        <text class="heading">Сообщество</text>
        <view class="profile" :style="styles.shadowBox">
            <view class="self_zone">
                <image :source="require('../assets/avatar.png')"/>
                <view :style="{marginLeft:25}">
                    <text class="name"> {{name}} {{surname}}</text>
                    <touchable-opacity class="btn"><text>Редактировать профиль</text></touchable-opacity>
                </view>
            </view>
            <view :style="{padding:10,flexDirection:'row'}">
                <text :style="{fontSize:16}">E-mail</text>
                <text :style="{fontSize:16,color:'#c4c4c4',marginLeft:130}">example@gmai.com</text>
            </view>
            <view :style="{padding:10,flexDirection:'row'}">
                <text :style="{fontSize:16}">Баллы</text>
                <text :style="{fontSize:16,color:'#c4c4c4',marginLeft:260}">{{score}}</text>
            </view>
        </view>

        <view class="raiting" :style="styles.shadowBox">
            <text class="heading">Рейтинг</text>
            <view class="centered">
                <view :style="{flexDirection:'row'}">
                    <text :style="{fontSize:14}">Место</text>
                    <text :style="{fontSize:14,marginLeft:85}">Имя</text>
                    <text :style="{fontSize:14,marginLeft:85}">Баллы</text>
                </view>
                <view v-for="(part,index) in people" :key="index" :style="{flexDirection:'row'}">
                    <text :style="{fontSize:17}">{{index+1}}</text>
                    <text :style="{fontSize:17,marginLeft:85}">{{part.name}}</text>
                    <text :style="{fontSize:17,marginLeft:55}">{{part.score}}</text>
                </view>
            </view>
        </view>

        <view class="raiting" :style="styles.shadowBox">
            <text class="heading">Обменять баллы</text>
            <view class="centered" :style="{flexDirection:'row'}">
                <view :style="{alignItems:'center',alignContent:'center'}">
                    <image
                        :source="require('../assets/gift_1.png')"
                    />
                    <text>Коврик для йоги</text>
                    <text>130 б.</text>
                </view>
                <view :style="{alignItems:'center',alignContent:'center',marginLeft:35}">
                    <image
                        :source="require('../assets/gift_2.png')"
                    />
                    <text>Блок для йоги</text>
                    <text>130 б.</text>
                </view>
            </view>
            <view class="centered" :style="{flexDirection:'row',marginTop:15}">
                <view :style="{alignItems:'center',alignContent:'center'}">
                    <image
                        :source="require('../assets/gift_2.png')"
                    />
                    <text>Блок для йоги</text>
                    <text>130 б.</text>
                </view>
                <view :style="{alignItems:'center',alignContent:'center',marginLeft:35}">
                    <image
                        :source="require('../assets/gift_1.png')"
                    />
                    <text>Коврик для йоги</text>
                    <text>130 б.</text>
                </view>
            </view>
        </view>
        <text>{{errors}}</text>
    </scroll-view>
</template>

<script>
import axios from 'axios';
import { StyleSheet } from 'react-native';
// import func from 'vue-editor-bridge';

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
            ],
            name:'',
            surname:'',
            score:'',
            errors:[]
        }
    },
    created:function(){
        axios.get("https://ululaapi.herokuapp.com/users/607b0fd605c1b73c1c5b00e2")
            .then(response => {this.name=response.data.name 
            this.surname=response.data.surname
            this.score=response.data.score})
            .catch(e=>{this.errors.push(e)})
    }
}
</script>

<style scoped>
.container {
  flex: 1;
  padding: 10;
  /* flex-direction: row; */
  margin-bottom:15;
}
.raiting{
    margin-top:25;
    padding:10;
   
}
.centered{
    /* align-content: center;
    align-items: center; */

    margin-top: 20;
    margin-left:20;
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
