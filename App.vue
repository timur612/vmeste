<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createDrawerNavigator,
  createStackNavigator,
} from "vue-native-router";

import HomeScreen from "./components/HomeScreen.vue";
import DetailsScreen from "./components/DetailScreen.vue";
import Main from "./components/Main.vue";

import Logview from "./components/registration/Logview.vue";
import Registration from "./components/registration/Registration.vue";
import LogIn from "./components/registration/LogIn.vue";

const DrawerNavigator = createDrawerNavigator(
  {
    View: {
      screen: Logview,
    },
    Registration: Registration,
    LogIn: LogIn,
    Main: Main
  },
  {
    initialRouteName: 'View'
  }
);

const StackNavigator = createStackNavigator(
  {
    Drawer: {screen:DrawerNavigator,
    navigationOptions: {
       title: 'Main',
       headerShown: false
     },},
     
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },
}
</script>

<style>
  
</style>