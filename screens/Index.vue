<template>
  <view class="container">
    <text class="heading">Home</text>
    <text class="text">Exercício rápido para entendimento de conceitos do Vue Native.</text>
  </view>
</template>

<script>
export default {
    props: {
        navigation: { type: Object }
    },
    methods: {
        goToAndroidTabNavigator() {
            this.navigation.navigate("AndroidTabs");
        }
    }
};
</script>

<style>
.container {
    align-items: center;
    justify-content: center;
    flex: 1;
    padding: 50px;
}
.heading {
    font-size: 30px;
    font-weight: bold;
    color: darkolivegreen;
    margin: 20px;
}
.text {
    text-align: center;
    margin: 10px;
}
</style>