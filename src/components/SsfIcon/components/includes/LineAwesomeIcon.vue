<template>
  <i :class="lineAwesomeClass" @click="$emit('click')"></i>
</template>

<script>

  import "../../assets/css/line-awesome.min.css"

  import {Icons} from '../../../../app/utils'

  export default {
    name: "SsfLineAwesomeIcon",

    props: {
      /* STRONG */
      weight: {
        type     : String,
        required : false,
        validator: (value) => ['regular', 'solid', 'light', 'brand', 'normal', 'twoTone'].includes(value)
      },

      /* ICON */
      icon    : { type: String, required: true, validator: (value) => Icons.lineAwesome.includes(value) },
      size    : { type: String, required: false, default: '' },
      fw      : { type: Boolean, required: false, default: false },
      animated: { type: Boolean, required: false, default: false },
      rotate  : { type: String, required: false, default: '' },
      pull    : { required: false, default: false }
    },

    computed: {

      lineAwesomeClass() {
        return `${this.strongClass}${this.iconClass}${this.sizeClass}${this.fwClass}${this.rotateClass}${this.animatedClass}${this.pullClass}`.trim()
      },

      strongClass() {
        return this.weight === 'regular' ? 'lar' : this.weight === 'light' ? 'lal' : this.weight === 'solid' ? 'las' : this.weight === 'brand' ? 'lab' : this.weight === 'twoTone' ? 'lad' : 'la'
      },

      iconClass() {
        return ` la-${this.icon}`
      },

      sizeClass() {
        return this.size ? ' la-' + this.size : ''
      },

      fwClass() {
        return this.fw ? ' la-fw' : ''
      },

      animatedClass() {
        return this.animated ? ' la-spin' : ''
      },

      rotateClass() {
        return ` ${this.rotate}`.trim()
      },

      pullClass() {
        return this.pull ? ` la-pull-${this.pull}` : ''
      }

    },
  }
</script>
