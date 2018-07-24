<template>
  <div class="button">
    <span v-for="item in list" :key="item.id" @click="zmClick">{{item.zm}}</span>
  </div>
</template>

<script scoped>
export default {
  name: 'SearchButton',
  props: {
    list: Array
  },
  methods: {
    zmClick (ev) {
      this.$emit('changeZm', ev.target.innerText)
    }
  }
}
</script>

<style lang="stylus" scoped>
  .button
    position: fixed
    right: 0
    top: 0.44rem
    font-size: 0.14rem
    width: 0.2rem
    text-align: center
    span
      display: block
      margin: 0.05rem 0
</style>
