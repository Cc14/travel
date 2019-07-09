<template>
    <ul class="list">
        <li 
        class="item" 
        v-for="item in letters" 
        :ref="item"
        :key="item"
        @click="handelLetterClick"
        @touchstart="handelTouchStart"
        @touchmove="handelTouchMove"
        @touchend="handelTouchEnd"
        >{{item}}</li>
    </ul>
</template>

<script>
export default {
  data() {
    return {
      isTauch: false,
      startY: "",
      timer: null
    };
  },
  updated() {
    this.startY = this.$refs["A"][0].offsetTop;
  },
  props: {
    cities: Object
  },
  computed: {
    letters() {
      const letters = [];
      for (let i in this.cities) {
        letters.push(i);
      }
      return letters;
    }
  },
  methods: {
    handelLetterClick(e) {
      //子组件通过emit事件给父组件传递内容
      this.$emit("changeKey", e.target.innerText);
    },
    handelTouchStart() {
      this.isTauch = true;
    },
    handelTouchMove(e) {
      if (this.isTauch) {
        if (this.timer) {
          clearTimeout(this.timer);
        }
        setTimeout(() => {
          const clientY = e.touches[0].clientY;
          const index = Math.floor((clientY - this.startY - 80) / 22);
          if (index >= 0 && index < this.letters.length) {
            this.$emit("changeKey", this.letters[index]);
          }
        }, 16);

        //console.log(clientY)
      }
    },
    handelTouchEnd() {
      this.isTauch = false;
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.list {
    position: absolute;
    top: 1.58rem;
    right: 0;
    bottom: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 0.4rem;
    color: $bgColor;

    .item {
        line-height: 0.44rem;
        text-align: center;
    }
}
</style>