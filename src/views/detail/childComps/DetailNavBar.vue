<template>
  <div class="detail-nav-bar">
    <nav-bar>
      <div slot="left" @click="backClick" class="arrow-left">
      </div>
      <div slot="center" class="title">
        <div class="title-item" v-for="(item, index) in titles" :key="index" :class="{active: currentIndex === index}"
          @click="itemClick(index)">
          {{item}}</div>
      </div>
    </nav-bar>

  </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar"
  export default {
    name: 'DetailNavBar',
    components: {
      NavBar
    },
    data() {
      return {
        titles: ['商品', '参数', '评论', '推荐'],
        currentIndex: 0
      }
    },
    methods: {
      itemClick(index) {
        this.currentIndex = index
        this.$emit('itemClick', index)
      },
      backClick() {
        this.$router.back()
      }
    },
  }
</script>
<style scoped>
  .title {
    display: flex;
    font-size: 15px;
  }

  .title .title-item {
    flex: 1;
  }

  .active {
    color: var(--color-high-text);
  }

  .back {
    margin-top: 10px;
  }
</style>