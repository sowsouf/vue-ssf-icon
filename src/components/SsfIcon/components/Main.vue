<template>
  <ssf-font-awesome-icon :icon="icon" :size="size" :fw="fw" :animated="animated" :rotate="rotate" :pull="pull"
                         :weight="weight" v-if="isFontAwesome" @click="$emit('click')"/>
  <ssf-line-awesome-icon :icon="icon" :size="size" :fw="fw" :animated="animated" :rotate="rotate" :pull="pull"
                         :weight="weight" v-else-if="isLineAwesome" @click="$emit('click')"/>
  <ssf-material-icon :icon="icon" :weight="weight" v-else-if="isMaterial" @click="$emit('click')"/>
</template>

<script>

  import "../assets/css/material.scss"

  import SsfFontAwesomeIcon from "./includes/FontAwesomeIcon";
  import SsfLineAwesomeIcon from "./includes/LineAwesomeIcon";
  import SsfMaterialIcon    from "./includes/MaterialIcon";

  export default {
    name: "SsfIcon",

    components: { SsfLineAwesomeIcon, SsfMaterialIcon, SsfFontAwesomeIcon },

    props: {
      type: { type: String, required: false, default: 'fa' },

      /* ICON */
      icon: { type: String, required: true },
      size: { type: String, required: false, default: '' },

      weight: {
        type     : String,
        required : false,
        validator: (value) => ['regular', 'solid', 'light', 'brand', 'normal', 'outlined', 'rounded', 'rounded', 'filled', 'twoTone', 'sharp'].includes(value)
      },

      /* FONT AWESOME */
      fw      : { type: Boolean, required: false, default: false },
      animated: { type: Boolean, required: false, default: false },
      rotate  : { type: String, required: false, default: '' },
      pull    : { required: false, default: false },
    },

    data() {
      return {}
    },

    watch: {
      icon() {
        this.$forceUpdate()
      },
    },

    computed: {
      isFontAwesome() {
        return this.type === 'fa'
      },

      isLineAwesome() {
        return this.type === 'la'
      },

      isMaterial() {
        return this.type === 'material'
      }
    },

  }
</script>

<style lang="scss">

  .ssf-row {
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    width: 100%;
  }

</style>
