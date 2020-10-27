<template>
  <div>
    <section class="hero is-medium">
      <div class="hero-body">
        <div class="container">
          <br />
          <div class="columns is-vcentered">
            <div class="column is-4">
              <div class="title">TORE LIQUIDITY</div>
              <div class="subtitle">Top 10 Provider</div>
            </div>

            <div class="column box is-offset-1">
              <b-table :data="data" :columns="columns" :hoverable="true">
                <b-table-column field="address" label="Address" v-slot="props">
                  {{ props.row.address }}
                </b-table-column>

                <b-table-column field="share" label="Share" v-slot="props">
                  {{ props.row.share }} %
                </b-table-column>
              </b-table>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>




<script>
import axios from "axios";

export default {
  data() {
    return {
      data: [],
    };
  },
  mounted() {
    axios({
      method: "GET",
      url:
        "https://api.ethplorer.io/getTopTokenHolders/0xb6825a020402f0ec2649d05aa22e65f9ec3198bb?apiKey=freekey&limit=10",
    }).then((response) => {
      this.data = response.data.holders;
    });
  },
};
</script>