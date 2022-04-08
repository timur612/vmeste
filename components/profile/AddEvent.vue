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

        
        <view style="marginTop:10%;paddingLeft:5%">
            <touchable-opacity style="marginBottom:15" :on-press="goToBack">
                <image
                    :source="require('../../assets/Events/arrow_left.png')"
                />
            </touchable-opacity>

            <text style="fontSize:20;fontWeight:bold">Карточка</text>

             <text-input
                    style="marginTop:5%"
                        class="input"
                        v-model="heading"
                        placeholder="Заголовок"
                    />
            
            <view style="marginTop:5%">
                <text>
                    Категории
                </text>
                <view style="flexDirection:row;marginTop:5%">
                    <touchable-opacity :class="b1 ?'badgeOrg':'badgeCard'" :on-press="()=>selectBadge(1)">
                        <text :class="b1 ?'tOrg':'tCard'">ЗОЖ</text>
                    </touchable-opacity>

                    <touchable-opacity :class="b2 ?'badgeOrg':'badgeCard'" style="marginLeft:5%" :on-press="()=>selectBadge(2)">
                        <text :class="b2 ?'tOrg':'tCard'">Образование</text>
                    </touchable-opacity>

                    <touchable-opacity :class="b3 ?'badgeOrg':'badgeCard'" style="marginLeft:5%" :on-press="()=>selectBadge(3)">
                        <text :class="b3 ?'tOrg':'tCard'">Дети и молодежь</text>
                    </touchable-opacity>
                </view>
            </view>

            <view style="marginTop:10%">
                <text style="fontSize:18;fontWeight:bold">Основная информация</text>

                <view style="marginTop:15">
                    <touchable-opacity class="btn" style="padding-left:2%;">
                        <text style="fontSize:15;color:white;">Выбрать дату</text>
                    </touchable-opacity>
                    <text style="marginTop:2%;marginLeft:3%;fontSize:20">{{date}}</text>
                </view>

                <view style="flexDirection:row;marginTop:5%">
                    <image
                        :source="require('../../assets/Profile/marker.png')"
                    />
                    <text style="marginLeft:10%;fontSize:16">{{location}}</text>
                </view>
            </view>
            <touchable-opacity class="btn" style="padding-left:25%;marginTop:20%" :on-press="saveEvent">
                <text style="fontSize:15;color:white;">Сохранить изменения</text>
            </touchable-opacity>
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
            platform: Platform.OS,
            id:'',
            organization:'',
            heading:'',
            badge:'',
            date:'07.04.22',
            location: 'г Якутск, ул Кулаковского, д 34/5',
            b1:false,
            b2:false,
            b3:false,
        }
    },
     props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            saveEvent(){
                const body = JSON.stringify({
                    organization: this.organization,
                    heading: this.heading,
                    badge: this.badge,
                    date: this.date,
                    location: this.location
                })
                axios.post('https://vmesteback.herokuapp.com/events',body,{headers: {"Content-Type": "application/json"  }})
                    .then(res=>{
                        this.navigation.navigate("Profile");
                    })
                    .catch(err=>{
                        console.log(err);
                    })
            },
            async getData(){
                this.id = await AsyncStorage.getItem('id');
                axios.get(`https://vmesteback.herokuapp.com/users/${this.id}`,{headers: {"Content-Type": "application/json"  }})
                    .then(res=>{
                        // this.name = res.data.name;
                        // this.email = res.data.email;
                        // this.org = res.data.org;
                        this.organization = res.data.organization;
                    })
                    .catch(err=>{
                        
                    })
            },
            goToBack: function() {
                this.navigation.navigate("Profile");
            },
            selectBadge(num){
                if(num==1){
                    this.b1=true;
                    this.badge = 'ЗОЖ';
                    this.b2=false;
                    this.b3=false;
                }
                if(num==2){
                   this.b1=false;
                    this.b2=true;
                    this.badge = 'Образование';
                    this.b3=false;
                }
                if(num==3){
                    this.b1=false;
                    this.b2=false;
                    this.b3=true;
                    this.badge = 'Дети и молодежь';
                }
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
            background-color:#75D811;
        }
.tOrg{
    color:white;
}
.tCard{
    color:#75D811;
}
.badgeCard{
            border-right-width:1;
            border-top-width:1;
            border-bottom-width:1;
            border-left-width:1;
            border-color:#75D811;
            border-radius:5;
            padding:2%;
            /* margin-left:3%; */
    }
.badgeOrg{
            background-color:#75D811;
            border-radius:5;
            padding:2%;
    }
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