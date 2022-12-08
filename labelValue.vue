<template>
  <div>
    <div class="label_value__span" :class="type">
      <span class="label_value__info">{{ title }}</span>
      <em v-if="required">*</em>
<!--      <infoTooltip v-if="description" :value="description"/>-->
    </div>
    <div :class="!line ? 'label_value__line label_value__span2': 'label_value__not-line label_value__span2'">
      <slot>Not Provided</slot>
    </div>
  </div>
</template>
<script>
export default {
  name: 'labelValue',
  props: {
    type: String,
    title: String,
    description: {
      type: String,
      default: ''
    },
    line: {
      type: Boolean,
      default: false
    },
    required: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style lang="scss" scoped>
.label_value__line {
  display: flex;
  flex-direction: column;
  border-bottom: 1px solid var(--info-color);
  width: max-content;
  min-width: 100%;
  min-height: 24px;
  justify-content: center;
}

.label_value__not-line {
  display: flex;
  flex-direction: column;
  min-width: 100%;
  width: auto;
  padding-top: 5px;
}

.label_value__span {
  font-size: 12px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  white-space: nowrap;
  text-transform: uppercase;
  letter-spacing: 0.11px;
  color: #00000080;
  opacity: 1;
  display: flex;
  align-items: flex-end;
}

.label_value__span2 {
  font-size: 14px;
  font-stretch: normal;
  min-height: 32px;
  font: normal normal normal 14px/20px Arial;
  letter-spacing: 0.25px;
  color: #000000;
}

.label_value__hidden {
  color: rgba(255, 255, 255, 0);
}

.hidden {
  color: rgba(255, 255, 255, 0);
}

.label_value__info {
  margin-right: 3px;
}
</style>
