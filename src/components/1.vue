<template>
  <div>
    <section class="hero is-medium">
      <div class="hero-body">
        <div class="container">
          <div class="columns is-vcentered">
            <div class="column is-6">
              <lottie-player
                src="https://ipfs.io/ipfs/QmTf1hyowJ1v8aGrQLdscCWjx5TEdq7Vn4rpi3UTTshgE4?filename=earn.json"
                background="transparent"
                speed="1"
                style="width: 100%; height: 100%"
                loop
                autoplay
              ></lottie-player>
            </div>
            <div class="column">
              <div class="columns is-vcentered is-multiline">
                <div class="column is-6">
                  <div class="box style1">
                    <strong>{{ holdings }} %</strong>
                    <hr />
                    TORE Liquidity Pool Ownership
                  </div>
                </div>
                <div class="column is-6">
                  <div class="box style1">
                    <strong>{{ torebalance }} TORE</strong>
                    <hr />
                    TORE BALANCE
                  </div>
                </div>

                <div class="column is-12">
                  <b-notification
                    type="is-info"
                    aria-close-label="Close notification"
                  >
                    Staking Starts 7th NOV
                  </b-notification>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>




<script>
export default {
  props: {
    holdings: {
      required: true,
      type: String,
    },
    torebalance: {
      required: true,
      type: String,
    },
  },
};
</script>


<style scoped>
.style1 {
  height: 150px;
}
</style>