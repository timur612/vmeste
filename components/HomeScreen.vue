<template>
<scroll-view :content-container-style="{contentContainer: {
        
    }}">
    <view :class="platform==='ios' ? 'mtIos' : 'mtAndroid'">
        <view class="header">
            <text class="text"> 
                вместе 
            </text>
            <touchable-opacity :class="platform==='ios' ? 'pimgIos' : 'pimgAndroid'" :on-press="goToProfile">
                
                <image
                    class="img"
                   
                    :source="require('../assets/profile-icon.png')"
                />
            </touchable-opacity>
        </view>

        <view style="paddingLeft:15;marginTop:30">
            <view class="carouser-card" style="flexDirection:row">
                
                <image
                    class="img"
                   
                    :source="require('../assets/Main/carouselimg.png')"
                />
                <view style="paddingLeft:12%">
                    <text :class="platform==='android'?'textCarMain':'textCarMainIos'">
                        Получи единую
                    </text>
                    <text :class="platform==='android'?'textCarMain':'textCarMainIos'">
                        карту волонтера
                    </text>
                    <text class="textCarMin">
                        скидки и так далее
                    </text>
                </view>
              
            </view>
        </view>

        <view style="marginTop:30">
            <view style="marginLeft:12;flexDirection:row">
                <text style="fontSize:20;fontWeight:bold">
                    Ивенты сейчас
                </text>
                <text style="marginLeft:65;marginTop:6;color:#75D811;fontSize:15">
                    Смотреть все
                </text>
            </view>
        </view>

        <view style="marginTop:30;paddingLeft:5%">

            <view class="card" v-for="(event,key) in events" :key="key">
                <image
                    class="img"
                    :source="require('../assets/Main/card_img.png')"
                />
                <touchable-opacity :on-press="goToEvent">
                    <view style="flexDirection:row;margin-top:4">
                        <view class="badgetext">
                            <text style="color:white;fontSize:12;">{{event.badge}}</text>
                        </view>
                        <view class="badgetext">
                            <text style="color:white;fontSize:12;"> {{event.score}} </text>
                        </view>
                    </view>

                    <text class="cardtext"> {{event.heading}} </text>

                    <view style="flexDirection:row;marginLeft:8;">
                        <image v-if="platform==='android'"
                            style="height:17;width:17"
                            :source="require('../assets/Main/calendar.png')"
                        />
                        <text style="color:#7E7E7E" :class="platform==='ios'?'bt':''">
                            07.04.22, 13:15 - 08.04.22, 13:15  
                        </text>
                    </view>

                    <view style="flexDirection:row;marginLeft:8;marginBottom:3;">
                        <image
                            v-if="platform==='android'"
                            style="height:17;width:17"
                            :source="require('../assets/Main/marker.png')"
                        />
                        <text style="color:#7E7E7E" >
                            г Якутск, ул Кулаковского, д 34/5 
                        </text>
                    </view>
                </touchable-opacity >

            </view>
            
          
        
        </view>

        <view style="marginTop:30">
            <view style="marginLeft:12;flexDirection:row">
                <text style="fontSize:20;fontWeight:bold">
                    Организаторы
                </text>
                <text style="marginLeft:65;marginTop:6;color:#75D811;fontSize:15">
                    Смотреть все
                </text>
            </view>
        </view>

        <view style="marginTop:30;paddingLeft:15;">

            <view class="organ" v-for="(organ,key) in organs" :key="key">
                <image
                            
                            :source="require('../assets/Main/profileimg.png')"
                        />
                <text style="width:250;marginLeft:15;"> {{organ.name}} </text>
            </view>

        </view>

        <view style="marginTop:30">
            <touchable-opacity class="btn" >
                <text style="fontSize:15;color:white">Верифицировать профиль</text>
            </touchable-opacity>
        </view>
   
    </view>
    </scroll-view>
</template>

<script>
import { Platform, StyleSheet } from 'react-native';
    export default {
        data(){
            return{
                events:[ {badge:'Дети и молодежь', score: '+2', heading: 'Уборка парковой территории'},
                        {badge:'Образование', score: '+2', heading: 'Помощь ветеранам'},
                        {badge:'ЗОЖ', score: '+2', heading: 'Самый длинны заголовок нужен здесь для переноса строки дааа'}

                ],
                organs: [{name:'Название'},{name:'Фонд “Добрые сердца”'},{name:'Центр по работе с волонтерами Республики Саха(Якутия)'}],
                platform: Platform.OS
            }
        },
        props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            goToEvent: function() {
                this.navigation.navigate("Event");
            },
            goToProfile: function() {
                this.navigation.navigate("Profile");
            },
        }
    }
</script>

<style scoped> 
    .bt{
        margin-bottom: -5%;
    }
    .textCarMainIos{
        margin-bottom:-35;
        font-size:18;
        color:#FFFFFF;
        font-weight: bold;
    }
    .mtIos{
        margin-top:2%;
    }
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
    .organ{
        flex-direction:row;
        border-right-width:1;
        border-left-width:1;
        border-top-width:1;
        border-bottom-width:1;
        border-color:#EFEFEF;
        width:330;
        margin-bottom:10;
        border-radius:10;
        padding:10;
    }
    .card{
        flex-direction:row;
        width:330;
        border-right-width:1;
        border-top-width:1;
        border-bottom-width:1;
        border-radius:10;
        border-color:#EFEFEF;
        margin-bottom:10;
    }
    .cardtext{
        width: 250;
        margin-top:5;
        margin-left:5;
        margin-bottom:7;
    }
    .badgetext{
        background-color:#75D811;
        border-radius:5;
        padding:5;
        margin-left:10;
        margin-top:5;
    }
    .text{
        font-size:35;
        color:#75D811;
        font-weight: bold;
    }
    .textCarMain{
        font-size:18;
        color:#FFFFFF;
        font-weight: bold;
    }
    .textCarMin{
        color:#FFFFFF;
        
    }
    .carouser-card{
        background-color:#75D811;
        padding-left:20;
        padding-top:20;
        padding-bottom:20;
        border-radius:10;
        width:330;
    }

</style>