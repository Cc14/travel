<template>
    <div>
        <div class="search">
            <input v-model="keyword" type="text" class="search-input" placeholder="请输入城市名或拼音">
        </div>
        <div class="search-content">
            <ul>
                <li v-for="(item, index) in list" :key="index">{{item.name}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  props: {
    cities: Object
  },
  data() {
    return {
      keyword: "",
      list: [],
      timer: null
    };
  },
  watch: {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.cities) {
          console.log(this.cities[i])
          this.cities[i].forEach((value) => {
              console.log(this.keyword)
            if (
              value.spell.indexOf(this.keyword) > -1 &&
              value.name.indexOf(this.keyword) > -1
            ) {
                
                console.log(value)
              result.push(value);
            }
          });
        }
        console.log(result)
        this.list = result;
      }, 100);
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.search {
    padding: 0 0.1rem;
    height: 0.72rem;
    background: $bgColor;

    .search-input {
        width: 100%;
        height: 0.62rem;
        line-height: 0.62rem;
        border-radius: 0.06rem;
        border: none;
        text-align: center;
    }
}

.search-content {
    z-index: 1;
    position: absolute;
    top: 1.58rem;
    left: 0;
    right: 0;
    bottom: 0;
    background: #ddd;
}
</style>