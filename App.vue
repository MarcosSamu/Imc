<template>
  <view class="container">
    <text class="text-color-primary">Como está meu IMC</text>
    <Status/>
    <comp/>
    
  </view>
</template>
<script>


import Comp from './components/comp.vue'
import Status from './components/status.vue'
import * as React from 'react';
import { AppRegistry } from 'react-native';
import { Provider as PaperProvider } from 'react-native-paper'
import { Button } from 'react-native-paper';
import { TextInput } from 'react-native-paper';

export default {
  components:{Comp, Status, PaperProvider}
}
</script>
<style>

.container {
  background-color: #ecf0f1;
  align-items: center;
  justify-content: center;
  flex: 1;
  margin-top: 20px;
  
}
.text-color-primary {
  color: #666
}
</style>
