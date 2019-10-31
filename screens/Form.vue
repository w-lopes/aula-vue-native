<template>
  <view class="container">
    <text class="heading">Consulta</text>
    <text class="text">ID (Existe do ID 1 ao 34)</text>
    <text-input class="input" v-model="text" />
    <text class="text" v-if="loading">Carregando</text>
    <button :on-press="onPress" title="Consultar ID" color="#10AD3C" />
  </view>
</template>

<script>
import { Alert } from 'react-native';

const outputAlert = (resp) => {
    Alert.alert(
        'Consulta',
        JSON.stringify(resp, null, 2),
        [
            {text: 'OK', onPress: () => console.log('OK...')},
        ],
        { cancelable: true }
    );
};

export default {
    data: () => {return {
        text: '',
        loading: false
    }},
    methods: {
        onPress () {
            if (!this.text) {
                outputAlert("Not found!");
                return;
            }
            this.loading = true;
            fetch("http://5db6fce5e2c76f0014a539bd.mockapi.io/api/aula/v1/Get/" + this.text, {
                method: "GET",
                headers: {
                    Accept: "application/json",
                }
            })
            .then(r => r.json()
            .then(json => {
                outputAlert(json);
                this.loading = false;
            }))
            .catch(er => {
                outputAlert(json);
                this.loading = false;
            });
        }
    }
}
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
.input {
    height: 40;
    width: 100;
    border-color: black;
    border-width: 1;
}
</style>