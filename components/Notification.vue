<template>
    <scroll-view :content-container-style="{contentContainer: {
        
    }}">
    <view :class="platform==='ios' ? 'mtIos' : 'mtAndroid'">
        <view class="header">
            <text class="text"> 
                вместе 
            </text>
            <touchable-opacity :class="platform==='ios' ? 'pimgIos' : 'pimgAndroid'" >
                
                <image
                    class="img"
                   
                    :source="require('../assets/profile-icon.png')"
                />
            </touchable-opacity>
        </view>

        <view style="marginLeft:5%;marginTop:5%;flexDirection:row">
            <text style="fontSize:20;fontWeight:bold">
                Уведомления
            </text>
            <view style="marginLeft:2%;borderRadius:50;backgroundColor:#75D811;paddingLeft:2.5%;paddingRight:2.5%;paddingTop:0.7%">
                <text style="color:white;">1</text>
            </view>
        </view>

        <view style="marginTop:10%;paddingLeft:6%">
                <view class="cardevent" v-for="(event,key) in notifs" :key="key">
                    <touchable-opacity >
                        <text class="cardtext"> {{event.heading}} </text>
                        <text style="width:24%;marginLeft:5%;color:#7E7E7E">{{event.date}}</text>
                    </touchable-opacity >
                </view>
            </view>
    </view>
    </scroll-view>
</template>

<script>
import { Platform } from 'react-native';
export default {
    data(){
        return{
            platform: Platform.OS,
            notifs:[ {date:'02.01.22', heading: 'Завтра начинается ивент “уборка парковой территории”'},
                        {date:'02.01.22', heading: 'Завтра начинается ивент “уборка парковой территории”'},
                        

                ],
        }
    },
}
</script>

<style scoped>
.cardevent{
        flex-direction:row;
        padding:2%;
        width:330;
        border-right-width:1;
        border-left-width:1;
        padding-bottom: 5   ;
        border-top-width:1;
        border-bottom-width:1;
        border-radius:10;
        border-color:#75D811;
        margin-bottom:10;
    }
    .cardtext{
        width: 250;
        font-size:15;
        font-weight: bold;
        margin-top:5;
        margin-left:5;
        margin-bottom:7;
    }
 /* COPY */
    .mtIos{
        margin-top:7%;
    }
    .mtAndroid{
        margin-top:10%;
    }
    .pimgIos{
        margin-left:52%;
        margin-top:4%;
    }
    .pimgAndroid{
        margin-left:175;
        margin-top:12;
    }
    .header{
        flex-direction:row;
    }
    .text{
        font-size:35;
        color:#75D811;
        font-weight: bold;
    }
    /* COPY */
</style>