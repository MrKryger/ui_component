<template>
  <div class="collapse-item" :class="getClass()">
    <div class="collapse-item__header" @click="click">
      <slot name="header"/>
      <div class="arrow-field" :class="isOpen ? 'arrow-field-active':''">
        <div
            class="arrow-field-icon"
            :class="isOpen ? 'active':'passive'"
            @click="isOpen = !isOpen" :size="12">
          <svg xmlns="http://www.w3.org/2000/svg" width="12" height="6.707" viewBox="0 0 12 6.707">
            <g transform="translate(18 15.25) rotate(180)">
              <path d="M12,8.75,17.854,14.6a.5.5,0,0,1-.708.708L12,10.164,6.854,15.311a.5.5,0,0,1-.708-.708Z"
                    transform="translate(0 -0.207)" fill="currentColor"/>
            </g>
          </svg>
        </div>
      </div>
    </div>
    <transition name="el-zoom-in-top">
      <div v-if="isOpen" class="collapse-card-block">
        <slot></slot>
      </div>
    </transition>
  </div>
</template>

<script>

export default {
  name: 'CoreCollapse',
  props: {
    open: {
      type: Boolean,
      default: false
    },
    type: {
      type: [Boolean, String],
      default: false
    },
    item: {
      type: Object
    }
  },
  data () {
    return {
      isOpen: this.open
    }
  },
  methods: {
    getClass () {
      const isOpen = this.isOpen ? 'collapse-open' : ''
      switch (this.type) {
        case 'light':
          return `collapse-light ${isOpen}`
        case 'grey':
          return `collapse-grey ${isOpen}`
        default:
          return `collapse-dark ${isOpen}`
      }
    },
    click () {
      this.isOpen = !this.isOpen
      if (this.item) this.$emit('keys', { item: this.item, open: this.isOpen })
      this.$emit('opens', this.isOpen)
    }
  }
}
</script>

<style lang="scss" scoped>

.collapse-item {
  .el-card {
    border-radius: 0;
  }
}

.collapse-item__header {
  width: 100%;
  display: flex;
  left: 0;
  align-items: center;
  justify-content: space-between;
  background-color: #FFF;
  color: #303133;
  cursor: pointer;
  border-bottom: 1px solid #EBEEF5;
  font-size: 13px;
  font-weight: 500;
  transition: border-bottom-color .3s;
  outline: 0;
  padding: 0 10px 0 20px;
  height: 75px;
  border-radius: 8px;
}

.arrow-field {
  border: 1px solid #FFFFFF1F;
  border-radius: var(--border-radius);
  color: #FFFFFF;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 20px;
}

.arrow-field-icon {
  transition: .3s;
  transform: rotate(90deg);
}

.arrow-field-active {
  background-color: #FFFFFF1F;
}

.active {
  transform: rotate(-90deg);
}

.collapse__radius {
  border-radius: 8px;
  transition: .3s;
}

.collapse-open {
  .collapse-item__header {
    transition: .3s;
    border-radius: 8px 8px 0 0;
  }
}

.collapse__color {
  background-color: #293543;
  background-image: none;
}

.block_light {
  .collapse-light {
    border-radius: 0;
  }
}

.collapse-card-block {
  border-radius: 0 0 6px 6px !important;
  padding: 20px;
  margin-bottom: 1rem;
  border-left: 1px solid var(--border-color);
  border-right: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
}

.collapse-dark .collapse-item__header {
  background-color: #293543;
}

.collapse-dark .collapse-item__header :deep(.date-text) {
  color: var(--light-color) !important;
}

.collapse-dark .collapse-item__header :deep(.icon) {
  background-color: #ffffff !important;
}

.collapse-light :deep(.collapse-item__header) {
  background-color: #ffffff;
  color: #000000;
  padding-right: 0;
}

.collapse-light :deep(.collapse-card-block) {
  border: none;
  background-color: #ffffff;
  padding: 0;
}

.collapse-light :deep(.collapse-item__header) {
  height: 64px;
  padding-left: 0;
}

.collapse-light :deep(.arrow-field) {
  color: #000000;
  background-color: #F7F7F7;
  margin-left: 10px;
}

.collapse-grey :deep(.collapse-item__header) {
  background-color: #F7F7F7;
  color: #000000;
  padding-right: 0;
  padding-left: 10px;
}

.collapse-grey :deep(.collapse-card-block) {
  border: none;
  background-color: #F7F7F7;
}

.collapse-grey :deep(.arrow-field) {
  color: #000000;
  background-color: #FFFFFF;
}

.collapse-grey :deep(.el-card) {
  background-color: #F7F7F7;
}

</style>
