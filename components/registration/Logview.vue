<template>
    <view>
        <view class="text-container">
            <text class="text">
                Добро
            </text>
            <text class="text">
                пожаловать
            </text>
        </view>
        <view class="img mt">
            <image
                :source="require('../../assets/registr/view.png')"
            />
        </view>

        <view class="img mt2">
            <image
                :source="require('../../assets/registr/logo.png')"
            />
        </view>

        <view style="paddingLeft:15; marginTop:40;">
            <touchable-opacity class="btn" :on-press="goTolog">
            <text style="fontSize:15;color:white">Войти</text>
            </touchable-opacity>

            <touchable-opacity class="btn2" :on-press="goToReg">
            <text style="fontSize:15;color:#11D81A">Зарегистрироваться</text>
            </touchable-opacity>
        </view>
    </view>
</template>

<script>
    import axios from 'axios'
    import AsyncStorage from '@react-native-async-storage/async-storage';
    export default {
        data(){
            return{
                id:''
            }
        },
        props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            goToReg: function() {
                this.navigation.navigate("Registration");
            },
            goTolog: function() {
                this.navigation.navigate("LogIn");
            },
            async check(){
                this.id = await AsyncStorage.getItem('id');
            }
        },
        created(){
            this.check();
            if(this.id!=''){
                this.navigation.navigate("Main");
            }
        }
    }
</script>

<style scoped>
    .text{
        font-size:40;
        color:#11D81A;
        font-weight: bold;
    }
    .text-container {
        margin-top: 50;
        margin-left:10;
    }
    .mt{
        margin-top: 40;
    }
    .mt2{
        margin-top: 50;
    }
    .img{
        
        margin-left:15%;
    }
    .btn{
        padding-left:148;
        padding-top:10;
        border-radius:10;
        width:330;
        height:40;
        background-color:#11D81A;
    }

    .btn2{
        margin-top:10;

        padding-left:100;
        padding-top:10;
        border-radius:10;

        border-left-width:1;
        border-right-width:1;
        border-top-width:1;
        border-bottom-width:1;

        border-color:#11D81A;
        width:330;
        height:40;
        background-color:white;
    }
</style>