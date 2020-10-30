<template>
  <b-navbar :fixed-top="true">
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
            target="_blank"
            href="https://info.uniswap.org/token/0xDDd4B9F27430FbEca4E4BCFC2859486714868473"
          >
            <strong>UNISWAP</strong>
          </a>
          <a
            class="button is-light"
            target="_blank"
            href="https://etherscan.io/token/0xDDd4B9F27430FbEca4E4BCFC2859486714868473"
          >
            ETHERSCAN
          </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>
