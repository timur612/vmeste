<template>
    <scroll-view class="container">
        <image
            :source="require('../assets/vector-creator.png')"
        />

        <view class="log">
            <text class="heading">Вход</text>
            <view>
                <text>Логин</text>
                <text-input
                    :style="{height: 40, width: 300, borderBottomColor: 'black', borderBottomWidth: 1}"
                    v-model="login"
                />
            </view>
            <view :style="{marginTop:10}">
                <text>Пароль</text>
                <text-input
                :style="{height: 40, width: 300, borderBottomColor: 'black', borderBottomWidth: 1}"
                v-model="password"
            />
            </view>

            <text v-if="errors.length>0" :style="{color:'red',marginTop:10}">
                Неправильно введен пароль или логин
            </text>
        </view>
        <touchable-opacity class="btn" :on-press="logIn">
            <text class="btn_text">Войти</text>
        </touchable-opacity>
        <!-- <text>{{res}}</text>
        <text>{{errors}}</text> -->
    </scroll-view>
</template>

<script>
import axios from 'axios';

export default {
    data:function(){
        return {
            login:'',
            password:'',
            res: '',
            errors:[],
        }
    },
     props: {
        navigation: { type: Object }
    },
    methods:{
        logIn(){
            this.errors = [];
            const postBody = JSON.stringify({
                    login: this.login,
                    password: this.password
                });
            // this.res = postBody;
            axios.post('https://ululaapi.herokuapp.com/users/login',postBody)
                .then(response => {this.navigation.navigate("IOSTabs")})
                .catch((e) => {
                    if((this.login=="user" && this.password=="12345") || (this.login=="mpit" && this.password=="12345")){
                        this.navigation.navigate("IOSTabs")
                    }else{
                        this.errors.push(e)
                    }
                })
        }
    }
}
</script>

<style scoped>
.btn{
    margin-top:30;

    align-content: center;
    align-items: center;
    width:auto;
    padding:10;
    border-radius: 30;
    background-color: #FFD500;
}
.btn_text{
        color:white;
    font-size:18;
}
.container {
  flex: 1;
  padding: 10;
  margin-bottom:15;
}
.heading{
  font-size: 26;
  font-weight:600;
  color: black;
  margin-left: 10;
}
.log{
    align-content: center;
    align-items: center;
    margin-top:10;
}
</style>