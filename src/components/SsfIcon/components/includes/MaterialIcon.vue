<template>
  <i class="material-icons" :class="materialClass" :style="`${size ? 'font-size: ' + size + 'px' : ''}`" @click="$emit('click')">{{ icon }}</i>
</template>

<script>

    import "../../assets/css/material.scss"

    import {Icons} from '../../../../app/utils'

    export default {
        name: "SsfMaterialIcon",

        props: {
            /* STRONG */
            outlined: { type: Boolean, required: false, default: true },
            rounded : { type: Boolean, required: false, default: false },
            filled  : { type: Boolean, required: false, default: false },
            twoTone : { type: Boolean, required: false, default: false },
            sharp   : { type: Boolean, required: false, default: false },

            /* ICON */
            icon: { type: String, required: true, validator: (value) => Icons.material.includes(value) },
            size: { type: Number, required: false, default: null },
        },

        computed: {

            materialClass() {
                return `${this.strongClass}`.trim()
            },

            strongClass() {
                return this.filled ? '' : `material-icons-${this.rounded ? 'round' : this.twoTone ? 'two-tone' : this.sharp ? 'sharp' : 'outlined'}`
            },

        },
    }
</script>

