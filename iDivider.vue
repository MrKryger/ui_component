<template>
  <div class="i-divider" :style="styleDivider"/>
</template>

<script>
export default {
  name: 'iDivider',
  props: {
    type: {
      type: String,
      default: 'solid',
      validator: (prop) => ['solid', 'dashed'].includes(prop)
    },
    indent: {
      type: Number,
      default: 20
    }
  },
  computed: {
    styleDivider () {
      return { 'border-style': this.type, margin: `${this.indent}px 0` }
    }
  }
}
</script>

<style lang="scss" scoped>
.i-divider {
  border: 0;
  border-top-width: 1px;
  border-color: #DCDFE6;
}
</style>
