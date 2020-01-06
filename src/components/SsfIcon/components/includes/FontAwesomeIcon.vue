<template>
  <i :class="fontAwesomeClass" @click="$emit('click')"></i>
</template>

<script>

  import "../../assets/css/font-awesome.min.css"
  // import "../assets/js/font-awesome.min.js"

  import {Icons} from '../../../../app/utils'

  export default {
    name: "SsfFontAwesomeIcon",

    props: {
      type: { type: String, required: false, default: 'fa' },

      /* STRONG */
      weight: {
        type     : String,
        required : false,
        validator: (value) => ['regular', 'solid', 'light', 'brand', 'normal'].includes(value)
      },

      /* ICON */
      icon    : { type: String, required: true, validator: (value) => Icons.fontAwesome.includes(value) },
      size    : { type: String, required: false, default: '' },
      fw      : { type: Boolean, required: false, default: false },
      animated: { type: Boolean, required: false, default: false },
      rotate  : { type: String, required: false, default: '' },
      pull    : { required: false, default: false }
    },

    computed: {

      fontAwesomeClass() {
        return `${this.strongClass}${this.iconClass}${this.sizeClass}${this.fwClass}${this.rotateClass}${this.animatedClass}${this.pullClass}`.trim()
      },

      strongClass() {
        return this.weight === 'normal' ? 'fa' : this.weight === 'light' ? 'fal' : this.weight === 'solid' ? 'fas' : this.weight === 'brand' ? 'fab' : 'far'
      },

      iconClass() {
        return ` fa-${this.icon}`
      },

      sizeClass() {
        return this.size ? ' fa-' + this.size : ''
      },

      fwClass() {
        return this.fw ? ' fa-fw' : ''
      },

      animatedClass() {
        return this.animated ? ' fa-spin' : ''
      },

      rotateClass() {
        return ` ${this.rotate}`.trim()
      },

      pullClass() {
        return this.pull ? ` fa-pull-${this.pull}` : ''
      }

    },
  }
</script>
