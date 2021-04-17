<template>
  <view class="container">
    <text class="heading">Тренировки</text>
    <view class="s-container">
         <view v-for="(day,index) in days" :key="index" class="ss-container" :class="{'cur_day_view':day.week_cur}" > 
            <text class="calendar" :class="{'cur_day':day.week_cur}">
                {{day.week_day}}
            </text>
            <text class="calendar" :class="{'cur_day_num':day.week_cur}">
                {{index+17}}
            </text>
        </view>
    </view>
    
    <scroll-view  :content-container-style="{contentContainer: {
  
    }}">
        <!-- Content goes here -->
    
    <view class="bar">
        <view class="bar_main">
            <view class="bar_color"></view>
        </view>
        <text class="bar-text">Выполнено тренировок: 1 из 3</text>
    </view>

    <view>
        <text class="heading">Сегодня</text>
        <view class="card shadow-box" :style="styles.shadowBox">
            <view class="card-img" >
                <image
                    :source="require('../assets/cardimg.png')"
                />
            </view>
            <view card="card-body">
                <text class="card_text">Йога для начинающих</text>
                <touchable-opacity :on-press="goToWebinar" :style="{flexDirection: 'row', justifyContent: 'flex-end'}">
                    <image
                        :style="{marginRight:20}"
                        :source="require('../assets/ArrowLeftOutline.png')"
                    />
                </touchable-opacity>
                <view class="s-container">
                    <!-- <svg-uri :width="50" :height="50" :xml="svg"></svg-uri> -->
                    <text class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/time.png')"
                    />15 мин</text>
                    <text  class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/ball.png')"
                    />5 баллов</text>
                    <text  class="card_text_p"><image
                        :style="{height:13,width:13}"
                        :source="require('../assets/notaaccept.png')"
                    />Не выполнено</text>
                </view>
            </view>
        </view>

        <text class="heading" :style="{fontSize:20,marginTop:10}">Можете также посмотреть</text>
        <scroll-view horizontal :style="{paddingBottom:10}">
            <view class="card shadow-box hor_card" :style="styles.shadowBox">
            <view class="card-img">
                <image
                    :source="require('../assets/cardimg2.png')"
                    :style="{width:360,borderTopLeftRadius:30,borderTopRightRadius:30}"
                />
            </view>
            <view card="card-body" >
                <text class="card_text">Кардио</text>
                <view class="s-container">
                    <text class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/time.png')"
                    />15 мин</text>
                    <text  class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/ball.png')"
                    />5 баллов</text>
                    <text  class="card_text_p"><image
                        :style="{height:13,width:13}"
                        :source="require('../assets/notaaccept.png')"
                    />Не выполнено</text>
                </view>
            </view>
            </view>

            <view class="card shadow-box hor_card" :style="styles.shadowBox">
            <view class="card-img">
                <image
                    :source="require('../assets/cardimg2.png')"
                    :style="{width:360,borderTopLeftRadius:30,borderTopRightRadius:30}"
                />
            </view>
            <view card="card-body" >
                <text class="card_text">Кардио</text>
                <view class="s-container">
                    <text class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/time.png')"
                    />15 мин</text>
                    <text  class="card_text_p"><image
                        :style="{height:12,width:12}"
                        :source="require('../assets/ball.png')"
                    />5 баллов</text>
                    <text  class="card_text_p"><image
                        :style="{height:13,width:13}"
                        :source="require('../assets/notaaccept.png')"
                    />Не выполнено</text>
                </view>
            </view>
            </view>
        </scroll-view>
        
    </view>
    </scroll-view>
  </view>
</template>

<script>
import Vue from 'vue-native-core'
import { SvgXml } from 'react-native-svg';

Vue.component('svg-uri', SvgXml)
import TimeSvg from '../assets/time.svg';

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
    borderRadius:30,
  },
});
export default {
    data:function(){
        return {
            id:'',
            svg:TimeSvg,
            styles,
            days: [{
                week_day:'пн',
                week_cur:false,},
                {
                week_day:'вт',
                week_cur:false,},
                {
                week_day:'ср',
                week_cur:false,},
                {
                week_day:'чт',
                week_cur:false,},
                {
                week_day:'пт',
                week_cur:false,},
                {
                week_day:'сб',
                week_cur:true,},
            ]
            
        }
    },
    props: {
        navigation: { type: Object }
    },
    created:function(){
        if(this.id===''){
             this.navigation.navigate("signin")
        }else{
            this.navigation.navigate("IOSTabs")
        }
        
    },
    methods: {
        goToWebinar(){
            this.navigation.navigate("web");
        },
    },
    components:{SvgXml}
}
</script>

<style>
.hor_card{
    margin-left:10;
}
.card{
    /* padding:15; */
    /* width:auto;  */
    margin-top:10;
    
}
.card-img{
    align-items: center;
}
.card-body{
   /* padding:25; */
   border-radius: 30;
   
   
}
.card_text{
    font-size: 18;
    margin-top:24;
    margin-left:24;
}
.card_text_p{
    margin-left:25;
    margin-bottom:15;
    padding-left:3;
}

.bar{
    width: auto;
    margin-top:10;
}
.bar-text{
    font-size: 17;
    color: #c4c4c4;;
    /* font-weight: bold; */
}
.bar_main{
    width: auto;
    height: 15;
    background-color: #EDEDED;
    border-radius: 30;
}
.bar_color{
    width:35%;
    height: 15;
    background-color: #0085ff;
    border-radius: 30;
}

.cur_day_num{
    border-radius: 30px;
    background-color: white;
    
}
.cur_day_view{
    background-color: #0085FF;
    border-radius: 30;
}
.cur_day{
    color:white;
}
.calendar{
    font-size: 20;
    padding: 10;
}

.container {
  flex: 1;
  padding: 10;
}
.ss-container{
    margin-left:14;
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
.text {
  text-align: center;
  margin: 10px;
}
</style>