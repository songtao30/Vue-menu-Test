<template>
  <div class="desc-info">
    <div v-for="(list,index) in changeInfo" :key="index">{{ list }}</div>
  </div>
</template>

<script>
export default {
  name: "DescInfo",
  props: ["selectIndex"],
  data: () => {
    return {
      info: [
        [],
        ['冲印1', '冲印2'],
        ['约拍1', '约拍2'],
        ['装饰相框', '小相框'],
        ['相册1', '相册2']
      ]
    }
  },
  computed: {
    changeInfo() {
      return this.info[this.selectIndex]
    }
  }
}
</script>

<style scoped>
.desc-info div {
  padding: 10px;
  background-color: #fff;
}
</style>