<template>
  <div class="TheCollapse">
    <button @click="nOfItems++">add el</button>
    <div class="header" @click="isMainOpen = !isMainOpen">Rozwiń mnie</div>
    <div class="content" :class="{ active: isMainOpen }">
      <div class="content__element">Lorem</div>
      <div class="content__element">Ipsum</div>
      <div class="content__element">Dolore</div>
      <div class="content__element" @click="isInnerOpen = !isInnerOpen">
        Rozwiń mnie
      </div>

      <div class="content__element__inner" :class="{ active: isInnerOpen }">
        <div class="content__element__inner__item">qwe</div>
        <div class="content__element__inner__item">asd</div>
        <div class="content__element__inner__item">zxc</div>
        <div
          class="content__element__inner__item"
          :key="n"
          v-for="n in nOfItems"
        >
          item {{ n }}
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const isMainOpen = ref(false);
const isInnerOpen = ref(false);
const nOfItems = ref(0);
</script>
<style lang="sass" scoped>
.TheCollapse
    display: flex
    flex-direction: column
    align-items: center
    .content
        color: blue
        max-height: 0
        overflow: hidden
        background: gray
        transition: max-height 500ms ease-in-out
        &.active
            max-height: 1000px
        &__element
            &__inner
                max-height: 0
                overflow: hidden
                transition: max-height 500ms ease-in-out
                &.active
                    max-height: 1000px
</style>
