<template>
<scroll-view :content-container-style="{contentContainer: {

    }}">
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
                        Вход
                    </text>
                </view>

                <view style="marginTop:30">
    
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

                    <touchable-opacity class="btn2" :on-press="logIn">
                        <text style="fontSize:15;color:white">Войти</text>
                    </touchable-opacity>
                    <text v-if="error" style="color:red">Вы неправильно ввели почту или пароль</text>
                    <text>{{text}}</text>
                </view>
                
                <view style="marginTop:170">
                    <touchable-opacity class="btn3" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{alignItems: 'center'}"
                                :source="require('../../assets/vk_icon.png')"
                            />
                            Войти через ВКонтакте
                        </text>
                    </touchable-opacity>
                    <touchable-opacity class="btn4" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{height:18,width:20,marginRight:30}"
                                :source="require('../../assets/google-icon.png')"
                            />
                            Войти через Google
                        </text>
                    </touchable-opacity>
                    <touchable-opacity class="btn5" >
                        
                        <text style="fontSize:15;color:white">
                        <image
                                :style="{height:19,width:20}"
                                :source="require('../../assets/gosicon.png')"
                            />
                            Войти через ГосУслуги
                        </text>
                    </touchable-opacity>
                </view>
            </view>
        </view>
       
    </view>
 </scroll-view>
</template>

<script>
import axios from 'axios'
import AsyncStorage from '@react-native-async-storage/async-storage';
    export default {
        data(){
            return{
                email:'',
                password:'',
                errors:'',
                text:'',
                error: false
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
            goToP: function() {
                this.navigation.navigate("Main");
            },
            async logIn(){
                this.errors = [];
                this.error = false;
                const body = JSON.stringify({
                    email: this.email,
                    password: this.password
                })
                
               
                        
                // this.res = postBody;
                axios.post('https://vmesteback.herokuapp.com/users/login',body,{headers: {"Content-Type": "application/json"  }})
                    .then(response => { 
                        AsyncStorage.setItem('id', response.data)
                        this.navigation.navigate("Main");
                    })
                    .catch((e) => {
                        
                            this.errors.push(e);
                            this.email = ''
                            this.password = ''
                            this.error = true;
                        
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

        padding-left:148;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#11D81A;
    }
    
    .btn3{
        margin-top:10;

        padding-left:75;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#0077FF;
    }
    .btn4{
        margin-top:10;

        padding-left:75;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#EA4335;
    }
    .btn5{
        margin-top:10;

        padding-left:75;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#0D67AF;
    }
</style>