<script>
export default {
  props: ['id', 'tag', 'added'],
  data() {
    return {
      active: false,
      error: false,
    };
  },
  methods: {
    activate() {
      this.active = true;
      setTimeout(() => {
        this.active = false;
      }, 3000);
    },
    select() {
      this.activate();
      this.$emit('select', this.tag);
    },
  },
};
</script>

<template>
  <div class="desire-item" :class="{active: active, error: error, added: added}" @click="select">
    {{tag}}
  </div>
</template>

<style lang="less"> 
@icon-path: "../images";

.desire-item {
  background-color: @white;
  background-image: url("@{icon-path}/desire_corner.png");
  background-position: left top;
  background-repeat: no-repeat;
  border-radius: @radius-xs;
  border: 1px solid @gray-light;
  color: @gray-dark;
  cursor: pointer;
  display: inline-block;
  font-size: 10px;
  font-style: normal;
  margin-bottom: @indent-sm;
  margin-right: @indent-xs;
  padding: 10px 5px 8px 6px;
  line-height: 1;
  text-transform: uppercase;

  &.deleted {
    background-color: @gray-light;
    text-decoration: line-through;
  }
  &.active {
    background-color: @yellow-light;
    border-color: @orange-light;
  }
  &.error {
    background-color: @pink-light;
    border-color: @pink;
  }
  &.added {
    background-image: url("@{icon-path}/desire_corner_blue.png");
    border-color: @purpur-dark;
  }
  &.process {
    background: @white;
    border-color: @light;
    color: @gray;
  }
}
</style>
