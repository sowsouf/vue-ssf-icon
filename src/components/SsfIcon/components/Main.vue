<template>
  <ssf-font-awesome-icon :icon="icon" :size="size" :fw="fw" :animated="animated" :rotate="rotate" :pull="pull"
                         :regular="regular" :solid="solid" :light="light" :brand="brand" :normal="normal"
                         v-if="isFontAwesome"/>
  <ssf-line-awesome-icon :icon="icon" :size="size" :fw="fw" :animated="animated" :rotate="rotate" :pull="pull"
                         :regular="regular" :solid="solid" :light="light" :brand="brand" :normal="normal"
                         :duo-tone="twoTone" v-else-if="isLineAwesome"/>
  <ssf-material-icon :icon="icon" :outlined="outlined" :filled="filled" :rounded="rounded" :two-tone="twoTone"
                     :sharp="sharp" v-else-if="isMaterial"/>
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

            /* FONT AWESOME */
            fw      : { type: Boolean, required: false, default: false },
            animated: { type: Boolean, required: false, default: false },
            rotate  : { type: String, required: false, default: '' },
            pull    : { required: false, default: false },
            // STRONG
            regular : { type: Boolean, required: false, default: true },
            solid   : { type: Boolean, required: false, default: false },
            light   : { type: Boolean, required: false, default: false },
            brand   : { type: Boolean, required: false, default: false },
            normal  : { type: Boolean, required: false, default: false },

            /* MATERIAL */
            outlined: { type: Boolean, required: false, default: true },
            rounded : { type: Boolean, required: false, default: false },
            filled  : { type: Boolean, required: false, default: false },
            twoTone : { type: Boolean, required: false, default: false },
            sharp   : { type: Boolean, required: false, default: false },
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
