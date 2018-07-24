<template>
  <div>
    <div class="search">
      <input v-model="inputValue" type="text" value="" class="searchContent" placeholder="请输入名称" @focus="isIvalue" />
      <span class="searchName">{{bookName}}</span>
      <span class="fanhui" @click="isNoIvalue">【返回】</span>
    </div>
    <div class="posSearchBox" ref="posSearchBox" v-show="isInputValue">
      <ul>
        <li v-for="item in searchList" :key="item">{{item}}</li>
        <li v-if="isNoDate">您查询的数据不存在</li>
      </ul>
    </div>
  </div>
</template>

<script scoped>
import BetterScroll from 'better-scroll'
export default {
  name: 'SearchInput',
  props: {
    list: Array
  },
  data () {
    return {
      inputValue: '',
      searchList: [],
      isInputValue: false,
      bookName: '斗破苍穹'
    }
  },
  methods: {
    isIvalue () {
      this.isInputValue = true
    },
    isNoIvalue () {
      this.isInputValue = false
      this.inputValue = ''
    }
  },
  computed: {
    isNoDate () {
      if (this.inputValue) {
        return !this.searchList.length
      }
    }
  },
  mounted () {
    this.scroll = new BetterScroll(this.$refs.posSearchBox)
  },
  watch: {
    inputValue () {
      const arr = []
      for (let i in this.list) {
        this.list[i].data.forEach((value) => {
          if (this.inputValue) {
            if (value.indexOf(this.inputValue) !== -1) {
              arr.push(value)
            }
          }
        })
      }
      this.searchList = arr
    }
  }
}
</script>

<style lang='stylus' scoped>
  .search
    font-size: 0.14rem
    overflow: hidden
    zoom: 1
    background: #abcdef
    height: 0.44rem
    position: fixed
    left: 0
    top: 0
    width: 3.75rem
    .searchContent
      float: left
      border: none
      background: #fff
      height: 0.24rem
      margin: 0.1rem
      width: 1.8rem
      padding: 0 0.1rem
      color: #ccc
      border-radius: 0.03rem
      font-size: 0.14rem
    .searchName
      float: left
      line-height: 0.44rem
      margin-left: 0.1rem
      color: #fff
      width: 0.8rem
      overflow: hidden
    .fanhui
      float: right
      margin-left: 0.05rem
      line-height: 0.44rem
      text-decoration: none
      color: #fff
      cursor: pointer
  .posSearchBox
    width: 3.75rem
    position: fixed
    top: 0.44rem
    left: 0
    bottom: 0
    overflow: hidden
    background: #fff
    z-index: 2
    font-size: 0.14rem
    ul
      li
        height: 0.3rem
        line-height: 0.3rem
        padding:0 0.1rem
        color: #666
</style>
