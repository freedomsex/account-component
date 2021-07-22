<script>
import _ from 'underscore';
import DesireItem from './DesireItem.vue';

export default {
  props: ['tags'],
  computed: {
    desires() {
      return this.$store.state.user.tags;
    },
  },
  methods: {
    add(tag) {
      if (!this.added(tag)) {
        this.$service.run('desires/save', tag);
      }
    },
    added(tag) {
      return _.contains(this.desires, tag);
    },
  },
  components: {
    DesireItem,
  },
};
</script>

<template>
  <div class="desire-list">
    <desire-item v-for="item in tags"
     :key="item.id"
     :tag="item.tag"
     :added="added(item.tag)"
     @select="add"/>
  </div>
</template>

<style lang="less">
.desire-list {
}
</style>
