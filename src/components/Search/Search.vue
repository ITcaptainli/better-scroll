<template>
  <div>
    <search-input :list="list"></search-input>
    <search-list :list="list" :listZm="listZm"></search-list>
    <search-button :list="list" @changeZm="changeZm"></search-button>
  </div>
</template>

<script scoped>
import SearchInput from './SearchInput'
import SearchList from './SearchList'
import SearchButton from './SearchButton'
export default {
  name: 'Search',
  data () {
    return {
      list: [
        {
          id: 1,
          zm: 'A',
          data: [
            '阿莫西林1',
            '啊啊啊啊啊12',
            '俺妹是男孩子1',
            '阿修罗1'
          ]
        },
        {
          id: 2,
          zm: 'B',
          data: [
            '比克大魔王3',
            '博客万岁3',
            '不说实话3',
            '便便很臭3',
            '北京3',
            '波兰的美好人生3',
            '补习班4',
            '被NTR了4',
            '别碰我咸猪手4'
          ]
        },
        {
          id: 3,
          zm: 'C',
          data: [
            '从你出走后5',
            '称你是儿子5',
            '层次感5',
            '才子异界游5',
            '曾经是个少年5',
            '吃屎的李勇5',
            '参见陛下5'
          ]
        },
        {
          id: 4,
          zm: 'D',
          data: [
            '但是不要你6',
            '都走了6',
            '道不同不相与谋6',
            '打死你个狗日的6',
            '当当当当1',
            '带队吃鸡1',
            '待我回来1',
            '点对点1'
          ]
        },
        {
          id: 5,
          zm: 'E',
          data: [
            '鹅2',
            '呃哈哈哈2',
            '恶人骨2'
          ]
        },
        {
          id: 6,
          zm: 'F',
          data: [
            '飞哥3',
            '飞走了3',
            '菲菲3',
            '妃子来啦3',
            '费人3',
            '飞哥2',
            '飞走了2',
            '菲菲2',
            '妃子来啦2'
          ]
        }
      ],
      listZm: ''
    }
  },
  components: {
    SearchInput,
    SearchList,
    SearchButton
  },
  methods: {
    changeZm (letter) {
      this.listZm = letter
    }
  }
}
</script>

<style>

</style>
