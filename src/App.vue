<template>
  <div id="app">
    <navbar />

    <div v-if="web3active">
      <v1 :holdings="holdings" :torebalance="torebalance" />
      <v2 />
      <v3 />
    </div>

    <div v-else>
      <web3 />
    </div>
  </div>
</template>

<script>
import navbar from "./components/navbar.vue";
import v1 from "./components/1.vue";
import v2 from "./components/2.vue";
import v3 from "./components/3.vue";
import web3 from "./components/web3.vue";

import Web3 from "web3";

export default {
  name: "App",

  data: () => ({
    torebalance: 1,
    holdings: 1,
    web3active: false,
  }),

  components: {
    navbar,
    v1,
    v2,
    v3,
    web3,
  },

  async mounted() {
    if (window.ethereum) {
      window.web3 = new Web3(window.ethereum);
      window.ethereum.enable();
      this.web3active = true;
    }

    const contractAbi = require("./assets/abi.json");
    const tokenAbi = require("./assets/token.json");

    const vidContract = new window.web3.eth.Contract(
      contractAbi,
      "0x6241e4206c28732dc7a21a83ca55d63cfa01d950"
    );
    const toreContract = new window.web3.eth.Contract(
      tokenAbi,
      "0xDDd4B9F27430FbEca4E4BCFC2859486714868473"
    );

    var useraddr = await window.web3.eth.getAccounts();

    var temp1 = await toreContract.methods.balanceOf(useraddr[0]).call();
    var temp2 = await Web3.utils.fromWei(temp1, "ether");
    this.torebalance = parseFloat(temp2).toFixed(3);

    const element1 = await vidContract.methods.balanceOf(useraddr[0]).call();

    const element2 = await vidContract.methods.totalSupply().call();
    this.holdings = ((element1 / element2) * 100).toFixed(3);
  },
};
</script>
