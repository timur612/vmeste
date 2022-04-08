<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createBottomTabNavigator,
  createStackNavigator
} from "vue-native-router";

import HomeScreen from './HomeScreen.vue'
import DetailScreen from './DetailScreen.vue'
import Notification from './Notification.vue'
import Search from './Search.vue'
import About from './About.vue'

import Event from './events/Event.vue'
import Function from './events/Function.vue'

import Profile from './profile/Profile.vue'
import AddEvent from './profile/AddEvent.vue'

import Icon from 'react-native-vector-icons/MaterialIcons';
import * as React from 'react';
// import Icon from 'react-native-vector-icons/FontAwesome';

const BottomTabNavigator = createBottomTabNavigator(
  {
    Home: {
      screen: HomeScreen,
      navigationOptions: {
      tabBarIcon:({focused}) =>{ return <Icon name="home" size={25} color={focused?"#75D811":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        },
       headerShown: false
     },
    },
    Notif:{
      screen: Notification,
      navigationOptions: {
       tabBarIcon:({focused}) =>{ return <Icon name="notifications" size={25} color={focused?"#75D811":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        },
       headerShown: false
     },
    },
    Search:{
      screen: Search,
      navigationOptions: {
       tabBarIcon:({focused}) =>{ return <Icon name="search" size={25} color={focused?"#75D811":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        },
       headerShown: false
     },
    },
    Menu:{
      screen: About,
      navigationOptions: {
       tabBarIcon:({focused}) =>{ return <Icon name="list" size={25} color={focused?"#75D811":"#00000"}/>},
        tabBarOptions:{
          showLabel:false,
        },
       headerShown: false
     },
    }
    
  },
  {
    initialRouteName: 'Home'
  }
);

const StackNavigator = createStackNavigator(
  {
    IOSTabs: {screen:BottomTabNavigator,navigationOptions: {
       headerShown: false
     },},
    Event: {screen:Event,navigationOptions: {
       headerShown: true
     },},
     Function: {screen:Function,navigationOptions: {
       headerShown: false
     },},
     Profile:{screen:Profile,navigationOptions: {
       headerShown: false
     },},
     AddEvent:{screen:AddEvent,navigationOptions: {
       headerShown: false
     },},
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components:{AppNavigator},
}
</script>

<style scoped>
.test{
  padding:100;
}
</style>