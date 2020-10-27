<template>
  <b-navbar>
    <template slot="brand">
      <b-navbar-item href="#"> Home </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-item href="https://t.me/financetore">Telegram </b-navbar-item>
      <b-navbar-item href="https://twitter.com/financetore"
        >Twitter
      </b-navbar-item>
    </template>

    <template slot="end">
      <b-navbar-item tag="div">
        <div class="buttons">
          <a
            class="button is-primary"
            href="https://info.uniswap.org/token/0x4474859f28a3ec265e2791b98a61f2bf9e0be295"
          >
            <strong>UNISWAP</strong>
          </a>
          <a
            class="button is-light"
            href="https://etherscan.io/token/0x4474859f28a3ec265e2791b98a61f2bf9e0be295"
          >
            ETHERSCAN
          </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>