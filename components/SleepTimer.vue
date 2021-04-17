<template>
    <scroll-view class="container">
        <text class="heading">Трекер сна</text>

        <view :style="{margin:15, flexDirection:'row'}">
            <view  v-for="(night,index) in nights" :key="index">
                <view class="vert_bar" :style="{height:night*20}"></view>
                <text :style="{marginLeft:30,marginTop:10,fontSize:16}">{{index+18}}</text>
            </view>
            
        </view>

        <view class="container" :style="styles.shadowBox">
            <text class="heading">Сегодня</text>

            <view class='clock'>
                <view class="big_ring">
                    <view class="big_ring" :style="{width:'100%',backgroundColor:'#9E52FF'}">
                        <view class="ring">
                            <text :style="{fontSize:35}">{{hour}} {{minute}}</text>
                            <text :style="{fontSize:14,color:'#c4c4c4'}">часов  минут</text>
                        </view>
                    </view>
                </view>
            </view>

            <view class="efficiency">
                <text :style="{fontSize:20,color:'white',marginTop:7,marginLeft:5}">{{eff_percent}}%</text>
                <view :style="{marginLeft:15}">
                    <text :style="{fontSize:20,color:'white'}">Эффективность сна</text>
                    <text :style="{fontSize:16,color:'white'}">21:11 - 7:38</text>
                </view>
            </view>

            <!-- <text class="heading">Цель по качеству сна</text> -->
            <touchable-opacity  class="addAlarm" :on-press="changeDate">
                <image
                    :style="{height:25,width:25}"
                    :source="require('../assets/alarm-clock.png')"
                />
                <text :style="{fontSize:18,marginLeft:15}">Добавить будильник</text>
            </touchable-opacity>
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
            nights:[8,7,2,4,8,9],
            styles,
            hour:'00',
            minute:'05',
            eff_percent:85,
        }
    },
    methods:{
        changeDate(){
            let date = new Date();
            let hours = date.getHours();
            let minutes = date.getMinutes();

            this.hour = hours;
            this.minute = minutes;
        }
    },
    mounted: function(){
        // this.$nextTick(this.changeDate)
    },
    components:{}
}
</script>

<style scoped>
.addAlarm{
      flex-direction: row;
    margin-top:15;
    padding:10;
    border-radius: 20;
    background-color: #c4c4c4;
}
.efficiency{
    flex-direction: row;
    margin-top:15;
    padding:10;
    border-radius: 20;
    background-color: #9E52FF;
}
.clock{
    align-content: center;
    align-items: center;
}
.big_ring{
    height: 200;
    width:200;

    background-color: #c4c4c4;
    border-radius: 100;
}
.ring{
    height: 170;
    width:170;

    margin-left: 16;
    margin-top:16;
    background-color: white;
    border-radius: 100;
    align-content: center;
    align-items: center;

    padding-top:55;
}

.vert_bar{

    width:15;
    background-color: #9E52FF;
    border-radius: 30;
    margin-left:30;
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
  margin-bottom:15;
}
</style>