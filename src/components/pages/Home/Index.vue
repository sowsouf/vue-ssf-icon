<template>
  <div class="home">
    <h1>Welcome to homepage, do what you want</h1>
    <ssf-icon icon="car" weight="solid" type="la" size="8x"/>
    <ssf-icon icon="car" weight="regular" size="8x"/>
    <ssf-icon icon="accessibility" type="material"/>
    Salut salut mes petits cornichons
  </div>
</template>

<script>

  import {SsfIcon} from "@/components/SsfIcon/";

  export default {

    name: 'Home',

    components: { SsfIcon },

    data() {
      return {}
    },

    created() {
    },

    methods: {}

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

  .home {
    padding-right: .75rem;
    padding-left: .75rem;
  }

</style>
