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
                   
                    :source="require('../../assets/profile-icon.png')"
                />
            </touchable-opacity>
        </view>

        <view style="paddingLeft:5%">
            <view class="profilecard">
                <image
                    :source="require('../../assets/Profile/profileimg.png')"
                />
                <view style="width:80%;marginLeft:10%">
                    <text style="fontSize:20;fontWeight:bold;color:white">
                        {{name}}
                    </text>
                    <view style="flexDirection:row">
                        <image
                            :source="require('../../assets/Profile/mail-icon.png')"
                        />
                        <text style="color:white;marginLeft:2%"> {{email}} </text>
                    </view>
                    <view style="flexDirection:row">
                        <image
                            :source="require('../../assets/Profile/phone-icon.png')"
                        />
                        <text style="color:white;marginLeft:2%">+7 (123) 456-78-90</text>
                    </view>
                </view>
            </view>

            <view style="marginTop:30">
                <view style="marginLeft:0;flexDirection:row">
                    <text style="fontSize:18;fontWeight:bold">
                        Отзывы организаторов
                    </text>
                    <text style="marginLeft:5;marginTop:6;color:#75D811;fontSize:15">
                        Смотреть все
                    </text>
                </view>
            </view>
            <view style="marginTop:10%">
                <view class="cardevent" v-for="(event,key) in events" :key="key">
                    <view>
                        <image
                            style="marginBottom:25%"
                            :source="require('../../assets/Profile/profile-icon.png')"
                        />
                        <text style="marginBottom:25%;color:#7E7E7E">
                            02.01.22
                        </text>
                        <view style="flexDirection:row">
                             <image
                                :source="require('../../assets/Profile/star-icon.png')"
                            />
                            <text>
                                {{event.score}}
                            </text>
                        </view>
                    </view>
                    <touchable-opacity >
                        <text class="cardtext"> {{event.heading}} </text>
                        <text style="width:24%;marginLeft:1%">{{event.text}}</text>
                    </touchable-opacity >
                </view>
            </view>

            <view style="marginTop:30">
                <view style="marginLeft:0;flexDirection:row">
                    <text style="fontSize:18;fontWeight:bold">
                        Ожидаемые ивенты
                    </text>
                    <text style="marginLeft:50;marginTop:6;color:#75D811;fontSize:15">
                        максимум 3
                    </text>
                </view>
            </view>
            <view style="marginTop:30;">

            <view class="card" v-for="(event,key) in myevents" :key="key">
                <image
                    class="img"
                    :source="require('../../assets/Main/card_img.png')"
                />
                <touchable-opacity >
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
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/calendar.png')"
                        />
                        <text style="color:#7E7E7E">
                            07.04.22, 13:15 - 08.04.22, 13:15  
                        </text>
                    </view>

                    <view style="flexDirection:row;marginLeft:8;marginBottom:3;">
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/marker.png')"
                        />
                        <text style="color:#7E7E7E">
                            г Якутск, ул Кулаковского, д 34/5 
                        </text>
                    </view>
                </touchable-opacity >
            </view>
            </view>


            <view style="marginTop:30">
                <view style="marginLeft:0;flexDirection:row">
                    <text style="fontSize:18;fontWeight:bold">
                        Законченные ивенты
                    </text>
                    <text style="marginLeft:25;marginTop:6;color:#75D811;fontSize:15">
                        Смотреть всё
                    </text>
                </view>
            </view>

            <view style="marginTop:30;">

            <view class="card" v-for="(event,key) in myeventsend" :key="key">
                <image
                    class="img"
                    :source="require('../../assets/Main/card_img.png')"
                />
                <touchable-opacity >
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
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/calendar.png')"
                        />
                        <text style="color:#7E7E7E">
                            07.04.22, 13:15 - 08.04.22, 13:15  
                        </text>
                    </view>

                    <view style="flexDirection:row;marginLeft:8;marginBottom:3;">
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/marker.png')"
                        />
                        <text style="color:#7E7E7E">
                            г Якутск, ул Кулаковского, д 34/5 
                        </text>
                    </view>
                </touchable-opacity >

            </view>
          
        
        </view>
        <view style="marginTop:30">
            <touchable-opacity class="btn" style="padding-left:20%;">
                <text style="fontSize:15;color:white;">Верифицировать профиль</text>
            </touchable-opacity>
        </view>
        <view style="marginTop:15">
            <touchable-opacity class="btn" style="padding-left:25%;">
                <text style="fontSize:15;color:white;">Стать организатором</text>
            </touchable-opacity>
        </view>
        </view>

        <view style="marginBottom:10%">
        </view>
    </view>
    </scroll-view>
</template>

<script>
import { Platform } from 'react-native';
import axios from 'axios';
import AsyncStorage from '@react-native-async-storage/async-storage';
export default {
    data(){
        return{
            name:'',
            email:'',
            id: '',
            platform: Platform.OS,
            events:[ {score:5,text:'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam...', heading: 'Центр по работе с волонтерами Республики Саха(Якутия)'},
                        {score:4.5,text:'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam...', heading: 'Волонтер штаба'},
                        

                ],
            myevents:[ {badge:'Дети и молодежь', score: '+2', heading: 'Уборка парковой территории'},

                ],
            myeventsend:[{badge:'Образование', score: '+2', heading: 'Помощь ветеранам'},
                        {badge:'ЗОЖ', score: '+2', heading: 'Самый длинны заголовок'}],

        }
    },
    methods:{
        async getData(){
            this.id = await AsyncStorage.getItem('id');
            axios.get(`https://vmesteback.herokuapp.com/users/${this.id}`,{headers: {"Content-Type": "application/json"  }})
                .then(res=>{
                    this.name = res.data.name;
                    this.email = res.data.email;
                })
                .catch(err=>{
                    
                })
        }
    },
    created(){
        this.getData();
    }
}
</script>

<style scoped>
.btn{
        
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#11D81A;
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
    .badgetext{
        background-color:#75D811;
        border-radius:5;
        padding:5;
        margin-left:10;
        margin-top:5;
    }
    .profilecard{
        margin-top:10%;
        padding: 10%;
        width:93%;
        background-color: #75D811;
        flex-direction: row;
        border-radius: 10;
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