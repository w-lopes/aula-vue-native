<template>
  <app-navigator></app-navigator>
</template>

<script>
import IndexScreen from "./screens/Index.vue";
import FormScreen from "./screens/Form.vue";
import {
    createAppContainer,
    createBottomTabNavigator,
    createMaterialTopTabNavigator,
    createStackNavigator
} from "vue-native-router";

const tabs = {
    Home: IndexScreen,
    Forms: FormScreen
};

const AppNavigator = createAppContainer(createBottomTabNavigator({
        Home: IndexScreen,
        Consulta: FormScreen,
    },{
        initialRouteName: 'Home',
    })
);
export default {
    components: { AppNavigator }
}
</script>