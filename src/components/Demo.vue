<template>
  <div class="menu-root">
    <div v-for="(item,index) in data" :key="index" class="data-warp">
      <div class="title">
        {{ item.title }}:
      </div>
      <div v-if="Array.isArray(item.desc)" class="desc">
        <select @change="selectChange($event)">
          <option v-for="(desc,i) in item.desc" :key="i" :value="desc">{{ desc }}
            <span v-if="i !== 0" class="arrow"> > </span>
          </option>
        </select>
        <DescInfo v-show="item.title === '商品分类'" :selectIndex="selectIndex"/>
      </div>
      <div v-else class="desc">
        <input :value="item.desc" type="text">
      </div>
    </div>
  </div>
</template>

<script>
import DescInfo from "@/components/DescInfo";

export default {
  name: "DemoCom",
  components: {DescInfo},
  data: () => {
    return {
      data: [
        {title: "商品类型", desc: ["非实物"]},
        {title: "商品分类", desc: ["请选择", "冲印", "约拍", "相框", "相册"]},
        {title: "出售价格", desc: 10},
        {title: "市场价格", desc: 15},
        {title: "商品库存", desc: 20},
        {title: "商品销量", desc: 99}
      ],
      selectIndex: 0
    }
  },
  methods: {
    selectChange(e) {
      this.selectIndex = e.target.selectedIndex
    }
  }
}
</script>

<style lang="less" scoped>
.menu-root {
  width: 700px;
  font-size: 20px;
  margin: 100px auto;
  background-color: #f2f2f2;

  .data-warp {
    display: flex;
    margin: 10px 0;
    padding: 20px 10px;
    box-sizing: border-box;

    .desc {
      display: flex;
      position: relative;

      select,
      input {
        padding: 5px 10px;
        margin-left: 15px;
        font-size: 20px;
      }
    }


  }
}
</style>