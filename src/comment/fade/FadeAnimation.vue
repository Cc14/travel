<template>
    <transition>
        <slot></slot>
    </transition>
</template>

<script>
    export default {
        
    }
</script>

<style lang="stylus" scoped>
.v-enter-active, .v-leave-active {
  transition: all  2s;
}
.v-enter, .v-leave-to {
  opacity 0
  transform translateX(100%)
}
// .v-enter
//     opacity 1
// .v-enter-active
//     transition: all  2s;
</style>