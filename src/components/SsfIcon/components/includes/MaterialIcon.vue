<template>
  <i class="material-icons" :class="materialClass" :style="`${size ? 'font-size: ' + size + 'px' : ''}`"
     @click="$emit('click')">{{ icon }}</i>
</template>

<script>

  import "../../assets/css/material.scss"

  import {Icons} from '../../../../app/utils'

  export default {
    name: "SsfMaterialIcon",

    props: {
      /* STRONG */
      weight: {
        type     : String,
        required : false,
        validator: (value) => ['outlined', 'rounded', 'rounded', 'filled', 'twoTone', 'sharp'].includes(value)
      },

      /* ICON */
      icon: { type: String, required: true, validator: (value) => Icons.material.includes(value) },
      size: { type: Number, required: false, default: null },
    },

    computed: {

      materialClass() {
        return `${this.strongClass}`.trim()
      },

      strongClass() {
        return this.weight === 'filled' ? '' : `material-icons-${this.weight === 'rounded' ? 'round' : this.weight === 'twoTone' ? 'two-tone' : this.weight === 'sharp' ? 'sharp' : 'outlined'}`
      },

    },
  }
</script>

