<template>
  <div id="app">
    <navbar />
    <v1 :holdings="holdings" :torebalance="torebalance" />
    <v2 />
    <v3 />
  </div>
</template>

<script>
import navbar from "./components/navbar.vue";
import v1 from "./components/1.vue";
import v2 from "./components/2.vue";
import v3 from "./components/3.vue";

import Web3 from "web3";

if (window.ethereum) {
  window.web3 = new Web3(window.ethereum);
  window.ethereum.enable();
}

const contractAbi = require("./assets/abi.json");
const tokenAbi = require("./assets/token.json");

const vidContract = new window.web3.eth.Contract(
  contractAbi,
  "0xb6825a020402f0ec2649d05aa22e65f9ec3198bb"
);
const toreContract = new window.web3.eth.Contract(
  tokenAbi,
  "0x4474859f28a3ec265e2791b98a61f2bf9e0be295"
);

export default {
  name: "App",

  data: () => ({
    torebalance: 1,
    element: 1,
    holdings: 1,
  }),

  components: {
    navbar,
    v1,
    v2,
    v3,
  },

  async mounted() {
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
