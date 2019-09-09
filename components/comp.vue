<template>
	
	<view>
		<TextInput
		 :style="{width:280,height: 50, borderColor: 'gray', borderWidth: 1, marginBottom:10, background:'transparent'}"
          v-model="peso" class="input"  label='Peso' color="#CC0000"
          selectionColor="#B992E7" underlineColor="#B992E7"
        />
        <TextInput
		 :style="{width:280,height: 50, borderColor: 'gray', borderWidth: 1,
		 marginBottom:10, color:'#CC0000'}"
          v-model="altura" class="input"  label='Altura' 
          selectionColor="#B992E7" underlineColor="#B992E7"
        />
        
        <Button
        	:on-press="calcula"
	        mode="contained"
	        color="#B992E7"
	        icon="camera"
    	>Calcula IMC</Button>

		<Text class="titulo">{{ titulo }}</Text>

		<Text class="descricao colorDesc1 result" v-if ="armazenaDados == 0" :style="{color:'black'}">Resultado</Text>
	    <Text class="descricao colorDesc1" v-else-if ="armazenaDados < 18.5" :style="{color:'red'}">{{ desc1 }}</Text>
	    <Text class="descricao colorDesc" v-else-if="armazenaDados > 18.5 && armazenaDados < 24.9" :style="{color:'blue'}">{{ desc2 }}</Text>
	    <Text class="descricao colorDesc" v-else-if="armazenaDados > 25 && armazenaDados < 29.9" :style="{color:'#FFD400'}">{{ desc3 }}</Text>
	    <Text class="descricao colorDesc" v-else-if="armazenaDados > 30 && armazenaDados < 39.9" :style="{color:'#BD9F39'}">{{ desc4 }}</Text>
	    <Text class="descricao colorDesc"  v-else-if="armazenaDados > 40 " :style="{color:'#D54444'}">{{ desc5 }}</Text>

	</view>
</template>

<style type="text/css">
	.input{

		text-align: center;
		background-color: transparent;
		color:red;
	}
	.descricao{
		text-align: center;
	}
	.descricao text{
		color:black;
	}
	.titulo{
		position: relative;
		top: 46px;
		font-size: 17px;
		left: 11px;
	}
	.colorDesc1{
		font-size: 20px;
		text-align: center;
	}
	.result{
		position: relative;
		top:60px;
	}
</style>
<script>
	import { Alert } from 'react-native'
	import * as React from 'react';
	import { AppRegistry } from 'react-native';
	import { Provider as PaperProvider } from 'react-native-paper'
	import { Button } from 'react-native-paper';
	import { TextInput } from 'react-native-paper';
	import { Appbar } from 'react-native-paper';
	export default{
		components:{PaperProvider, Button,TextInput},

		data:function(){
			return{
				peso:'',
				altura:'',
				titulo:'IMC Classificação Obesidade (grau)',
				desc1:'IMC menor que 18,5 	Magreza 0',
				desc2:'IMC entre 18,5 e 24,9 Normal 0',
				desc3:'IMC entre 25,0 e 29,9 Sobrepeso I',
				desc4:'IMC entre 30,0 e 39,9 Obesidade II',
				desc5:'IMC maior que 40,0 Obesidade Grave III',
				armazenaDados:''
			}
		},

		methods:{
			calcula: function(){
				let imc = parseFloat(this.peso) / (parseFloat(this.altura) ** 2)
				imc = imc.toFixed(2)


				this.armazenaDados = imc
				Alert.alert(
					'Calculo de IMC',
					`${this.armazenaDados}`,

				)
				if (isNaN(this.peso) == true || isNaN(this.altura) == true){
					alert('Carácter não é numérico ou use  \n  ( . ) no lugar da ( , )')

				}
				else if (this.peso == '' && this.altura == ''){
					alert("Espaço em branco")
				}
				else if (imc == 0){
					alert('Valor não válido')
				}
				
			},
		},
		
	}
</script>