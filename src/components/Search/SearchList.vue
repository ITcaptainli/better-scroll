<template>
  <div class="list">
    <div class="listDiv" ref="searchList">
      <div>
        <div class="listDivCon">
          <div class="h1">当前选择</div>
          <div class="content">
            <span>俺没事男孩子</span>
          </div>
        </div>
        <div class="listDivCon" v-for="item in list" :key="item.id" :ref="item.zm">
          <div class="h1">{{item.zm}}</div>
          <div class="content">
            <span v-for="itemName in item.data" :key="itemName">{{itemName}}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script scoped>
import BetterScroll from 'better-scroll'
export default {
  name: 'SearchList',
  props: {
    list: Array,
    listZm: String
  },
  mounted () {
    this.scroll = new BetterScroll(this.$refs.searchList)
  },
  watch: {
    listZm () {
      if (this.listZm) {
        const el = this.$refs[this.listZm][0]
        this.scroll.scrollToElement(el)
      }
    }
  }
}
</script>

<style lang='stylus' scoped>
  .list
    .listDiv
      position: fixed
      left: 0
      top: 0.44rem
      bottom: 0
      width: 3.75rem
      font-size: 0.14rem
      overflow: hidden
      .listDivCon
        margin: 0.1rem
        .h1
          height: 0.4rem
          line-height: 0.4rem
          padding: 0 0.1rem
          font-size: 0.16rem
        .content
          overflow: hidden
          zoom: 1
          span
            float: left
            padding: 0.1rem 0.15rem
            border: 1px solid #ccc
            margin: 0.05rem
</style>
