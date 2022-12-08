<template>
  <div class="loader-block">
    <di
      v-if="isLoader"
      class="is-loading">
      LoadingIcon
    </di>
    <div v-else class="loader-block-flex">
      No Data
      <button @click="$emit('reload')">reload</button>
    </div>
  </div>
</template>

<script>
import { Loading } from '@element-plus/icons-vue'
import { mapGetters } from 'vuex'
import ButtonIcon from '@/shared/button/ButtonIcon.vue'

export default {
  name: 'loaderBlock',
  components: {
    ButtonIcon,
    Loading
  },
  computed: {
    ...mapGetters({
      isLoader: 'isLoader'
    })
  }
}
</script>

<style lang="scss" scoped>
.loader-block {
  padding: 20px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border: var(--border);
  border-radius: var(--border-radius);
}
.loader-block-flex {
  display: flex;
  align-items: center;
}
.loader-block-flex button {
  margin-left: 10px;
}
</style>
