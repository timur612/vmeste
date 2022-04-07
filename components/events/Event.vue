<template>
<scroll-view :content-container-style="{contentContainer: {
        paddingVertical: 20
    }}">
    <view :class="platform==='ios' ? 'mtIos' : 'mtAndroid'">
        <view class="header">
            <text class="text"> 
                вместе 
            </text>
            <touchable-opacity :class="platform==='ios' ? 'pimgIos' : 'pimgAndroid'">
                
                <image
                    class="img"
                   
                    :source="require('../../assets/profile-icon.png')"
                />
            </touchable-opacity>
        </view>

        <view class="card">
            <image
                    :source="require('../../assets/Events/event-img.png')"
            />

            <view>
                <image
                    style="marginLeft:10"
                    :source="require('../../assets/Events/share-icon.png')"
                />
                <view style="flexDirection:row">
                    <view class="badgetext" style="marginTop:15">
                        <text style="color:white;fontSize:12;">ЗОЖ</text>
                    </view>
                    <view class="badgetext" style="marginTop:15">
                        <text style="color:white;fontSize:12;">Образование</text>
                    </view>
                </view>

                <view style="width:125">
                    <view class="badgetext" style="marginTop:5">
                        <text style="color:white;fontSize:12;">Дети и молодежь</text>
                    </view>
                </view>

                <view style="width:200;marginLeft:10;marginTop:15">
                    <text style="fontWeight:bold;fontSize:15">Самый длинны заголовок нужен здесь для переноса ст</text>
                </view>
            </view>
        </view>

        <view style="marginTop:30">
            <view style="marginLeft:12;flexDirection:row">
                <text style="fontSize:20;fontWeight:bold">
                    Основная информация
                </text>
            </view>

            <view style="marginTop:30;paddingLeft:15;">

            <view class="organ" v-for="(info,key) in infos" :key="key">
                    <image
                        style="height:26;width:26"
                        :source="info.img"
                    />
                    <text style="width:250;marginLeft:15;"> {{info.name}} </text>
                </view>

            </view>
        </view>

        <view>
            <view style="marginLeft:12;flexDirection:row">
                <text style="fontSize:20;fontWeight:bold">
                    Описание
                </text>
            </view>
            <view style="width:350;marginLeft:12">
                <text style="marginLeft:5"> 
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
                </text>
                
            </view>
        </view>

        <touchable-opacity :class="platform==='anroid' ? 'funcbtn':'funcbtnIos'" :on-press="goToFunc">
            <text style="color:white;fontSize:17">
                Смотреть функции
            </text>
        </touchable-opacity>
    </view>
</scroll-view>
</template>

<script>
import { Platform } from 'react-native';
export default {
    data(){
        return{
            infos:[{name:'Центр по работе с волонтерами Республики Саха(Якутия)', img:require('../../assets/Events/profileimg.png')},
                {name:'07 апреля 2022 13:15 - 08 апреля 2022 13:15', img:require('../../assets/Events/calendar-icon.png')},
                {name:'г Якутск, ул Кулаковского, д 34/5', img:require('../../assets/Events/marker-icon.png')}
            ],
            platform: Platform.OS
        }
    },
     props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            goToFunc: function() {
                this.navigation.navigate("Function");
            },
        }
}
</script>

<style scoped>
    /* COPY */
    
    .mtAndroid{
        margin-top:10%;
    }
    .pimgIos{
        margin-left:50%;
        margin-top:12%;
    }
    .pimgAndroid{
        margin-left:130;
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

    .funcbtn{
        /* position:absolute;
        bottom:0;
        left:8%; */

        padding-left:70;
        padding-right: 70;
        padding-top:12;
        padding-bottom:12;

        border-radius:10;
        background-color: #75D811;
    }
    .funcbtnIos{
         position:absolute;
        bottom:0;
        left:8%;

        padding-left:70;
        padding-right: 70;
        padding-top:2;
        padding-bottom:2;

        border-radius:10;
        background-color: #75D811;
    }
    .card{
        flex-direction:row;
        margin-top:30;
    }
    .badgetext{
        background-color:#75D811;
        border-radius:5;
        padding:5;
        margin-left:10;
        margin-top:5;
    }
    .organ{
        flex-direction:row;
    
        width:330;
        margin-bottom:5;
        border-radius:10;
        padding:10;
    }
    
</style>