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

        <view style="paddingLeft:5%;marginTop:10%">
            <text-input
                        class="input"
                        placeholder="Поиск"
                    />
        </view>
        <image
            style="marginLeft:10%"
                :source="require('../assets/search.png')"
            />
        <view style="marginLeft:27%;marginTop:30%">
            <text style="fontSize:25;color:#75D811">
                Начните поиск
            </text>
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
        
        }
    },
}
</script>

<style scoped>
.input{
        background-color:#EFEFEF;
        padding-left:10;
        margin-bottom:10;
        border-radius:10;
        width:330;
        height:40;
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