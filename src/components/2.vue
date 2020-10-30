<template>
  <div>
    <section class="hero is-medium">
      <div class="hero-body">
        <div class="container">
          <div class="columns is-vcentered">
            <div class="column is-2">
              <div class="box style1">
                <strong>TORE PRICE</strong>
              </div>
            </div>
            <div class="column is-offset-1">
              <trend
                :data="arr"
                :gradient="['#6fa8dc', '#42b983', '#2c3e50']"
                :padding="8"
                :radius="8"
                :stroke-width="2"
                auto-draw
                smooth
              >
              </trend>
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
  data: () => ({
    arr: [],
  }),
  mounted() {
    axios({
      url: "https://api.thegraph.com/subgraphs/name/uniswap/uniswap-v2",
      method: "post",
      data: {
        query: `{ tokenDayDatas( last: 15 where: { token: "0xDDd4B9F27430FbEca4E4BCFC2859486714868473" }) { id priceUSD } }`,
      },
    }).then((result) => {
      var datax = result.data.data.tokenDayDatas;

      datax.forEach((element) => {
        if (element.priceUSD > 0) {
          this.arr.push(parseFloat(element.priceUSD));
        }
      });
    });
  },
};
</script>
