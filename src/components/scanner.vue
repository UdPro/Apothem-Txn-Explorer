<template>
  <v-container>
	<h1 class="mt-2">Apothem Transaction Explorer</h1>
	<v-row class="mt-5">
		<v-col>
			<v-text-field
				v-model="txnNumber"
				outlined
				clearable
			>
			</v-text-field>
		</v-col>
		<v-col
			cols="1"
			class="d-flex align-center mt-n8"
		>
			<v-btn 
				x-large
				:loading = "buttonLoading"
				color="primary"
				@click="getTxn()"
			>Search</v-btn>
		</v-col>
	</v-row>
	<v-card
		v-if="trx_info !=  undefined "
	>
		<v-card-title>Transcation Information</v-card-title>
		<v-divider></v-divider>
		<v-row
			no-gutters
			v-for="(key, value) in trx_info"
			:key="value"
		>
			<v-col
				cols="2"
			>
				<v-card-subtitle class="font-weight-bold">{{ value }}</v-card-subtitle>
			</v-col>
			<v-col>
				<v-card-subtitle class="text-break">{{ key }}</v-card-subtitle>
			</v-col>
		</v-row>
	</v-card>
  </v-container>
</template>

<script>
  const Web3 = require('xdc3');
  const web3 = new Web3(new Web3.providers.HttpProvider("https://rpc.apothem.Network"));
  
  export default {
    name: 'scanner',

    data: () => ({
		txnNumber: null,
		buttonLoading: false,
		trx_info: undefined,
		value: "hello",
     }),
     methods:{
		getTxn: async function() {
			this.buttonLoading = true;
			const result = await web3.eth.getTransaction(this.txnNumber);
			this.trx_info = result;
			this.buttonLoading = false;
		},
    }
  }
</script>
