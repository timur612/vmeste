<template>
    <view class="main">
        <view style="marginTop:50;marginLeft:80">
            <image
                :source="require('../../assets/logo.png')"
            />
        </view>

        <view class="undermain">
            <view style="paddingLeft:15;marginTop:70">
                <view>
                    <text class="text"> 
                        <touchable-opacity style="marginRight:10" :on-press="goToMain">
                            <image
                                :style="{alignItems: 'center'}"
                                :source="require('../../assets/left_arrow.png')"
                            />
                        </touchable-opacity> 
                        Регистрация
                    </text>
                </view>

                <view style="marginTop:30">
                    <text-input
                        class="input"
                        v-model="name"
                        placeholder="ФИО"
                    />
                     <text-input
                        class="input"
                        v-model="email"
                        placeholder="Почта"
                    />
                     <text-input
                        class="input"
                        v-model="password"
                        placeholder="Пароль"
                        secureTextEntry
                    />
                     <text-input
                        class="input"
                        placeholder="Повторите пароль"
                        secureTextEntry
                    />
                    <touchable-opacity class="btn2" :on-press="registr">
                        <text style="fontSize:15;color:white">Зарегистрироваться</text>
                    </touchable-opacity>
                    <text>{{text}}</text>
                </view>

                <view style="marginTop:70">
                    <touchable-opacity class="btn3" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{alignItems: 'center'}"
                                :source="require('../../assets/vk_icon.png')"
                            />
                            Регистрация через ВКонтакте
                        </text>
                    </touchable-opacity>
                    <touchable-opacity class="btn4" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{height:18,width:20,backgroundColor:'#FFFFFF',marginRight:30}"
                                :source="require('../../assets/google-icon.png')"
                            />
                            Регистрация через Google
                        </text>
                    </touchable-opacity>
                    <touchable-opacity class="btn5" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{height:19,width:20}"
                                :source="require('../../assets/gosicon.png')"
                            />
                            Регистрация через ГосУслуги
                        </text>
                    </touchable-opacity>
                </view>
            </view>
        </view>
    </view>
</template>

<script>
import axios from 'axios'
import AsyncStorage from '@react-native-async-storage/async-storage';
    export default {
        data(){
            return{
                name:'',
                email:'',
                text:'',
                password:'',
                errors: []
            }
        },
        props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            goToMain: function() {
                this.navigation.navigate("View");
            },
            async registr(){
                this.errors = [];
                const body = JSON.stringify({
                        email: this.email,
                        password: this.password,
                        name: this.name,
                        lastName: ''
                    });
                axios.post('https://vmesteback.herokuapp.com/users',body,{headers: {"Content-Type": "application/json"  }})
                    .then(response => {
                        AsyncStorage.setItem('id', response.data.user._id);
                        
                        this.navigation.navigate("Main")
                        }
                        )
                    .catch((e) => {
                        
                            this.errors.push(e);
                            // this.error = true;
                        
                    })
            }
        }
    }
</script>

<style scoped>
    .main{
        height:100%;
        background-color:#75D811;
    }
    .text{
        font-size:35;
        color:#11D81A;
        font-weight: bold;
    }
    .undermain{
        margin-top:30;
        border-radius:30;
        height:100%;
        background-color:white;
    }
    .input{
        background-color:#EFEFEF;
        padding-left:10;
        margin-bottom:10;
        border-radius:10;
        width:330;
        height:40;
    }
    .btn2{
        margin-top:10;

        padding-left:105;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#11D81A;
    }
    
    .btn3{
        margin-top:10;

        padding-left:45;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#0077FF;
    }
    .btn4{
        margin-top:10;

        padding-left:45;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#EA4335;
    }
    .btn5{
        margin-top:10;

        padding-left:45;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#0D67AF;
    }
</style>