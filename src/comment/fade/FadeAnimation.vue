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
  transition: opacity .5s;
}
.v-enter, .v-leave-to{
  opacity: 0;
}

</style>