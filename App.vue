<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createBottomTabNavigator,
  createStackNavigator
} from "vue-native-router";

import HomeScreen from './components/HomeScreen.vue'
import TabBar from './components/TabBar.vue'
import Diary from './components/Diary.vue'
import Profile from './components/Profile.vue'
import Webinar from './components/Webinar.vue'

import MainIcon from './assets/main.svg'
import Icon from 'react-native-vector-icons/MaterialIcons';
import * as React from 'react';
// import Icon from 'react-native-vector-icons/FontAwesome';

const BottomTabNavigator = createBottomTabNavigator(
  {
    Home: {
      screen: HomeScreen,
      navigationOptions:{
        tabBarIcon:({focused}) =>{ return <Icon name="run-circle" size={25} color={focused?"#0085FF":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        },
        
      },
    },
    Diary: {
      screen: Diary,
      navigationOptions: {
        tabBarIcon:({focused})=> {return <Icon name="book" size={25} color={focused?"#4FC532":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        }
      }
      },
    Sleep: {
      screen:TabBar,
      navigationOptions:{
        tabBarIcon:({focused})=> {return <Icon name="snooze" size={25} color={focused?"#9E52FF":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        }
      }
      },
    Profile: {
      screen:Profile,
      navigationOptions:{
        tabBarIcon:({focused})=> {return <Icon name="account-circle" size={25} color={focused?"#FFD500":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        }
      }
      },
    
  },
  {
    initialRouteName: 'Home'
  }
);

const StackNavigator = createStackNavigator(
  {
    IOSTabs: BottomTabNavigator,
    web: Webinar
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components:{AppNavigator}
}
</script>

<style scoped>
.test{
  padding:100;
}
</style>