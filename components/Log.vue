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
            axios.post('https://ululaapi.herokuapp.com/users/login',{
                body:{
                    login: this.login,
                    password: this.password
                }
            })
            .then(response => {this.res=response})
            .catch(e => {
                // this.errors.push(e)
                this.navigation.navigate("IOSTabs")
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