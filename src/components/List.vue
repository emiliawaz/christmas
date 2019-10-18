<template>
  <div class="c-list" :class="isPink ? 'c-list--pink' : ''">
    <h2 class="c-list__title">{{ title }}</h2>
    <ol class="c-list__content" v-if="list.length">
      <li 
        class="c-list__item"
        v-for="(item, i) in list"
        :key="`${item}-${i}`">
        {{ item }}</li>
    </ol>
    <div class="c-list__content c-list__content--empty" v-else>
      List is empty
    </div>
  </div>
</template>

<script>
export default {
  name: 'list',

  props: {
    list: {
      type: Array,
      default: () => []
    },

    isPink: {
      type: Boolean,
      default: false
    },

    title: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.c-list {
  background: #ffe9bada;
  min-width: 40%;
  border-radius: .7rem;
  margin: 3rem auto;
  text-align: center;
  font-size: 2rem;
  display: inline-block;

  &.c-list--pink {
    background: #ffbae2e3;
    .c-list__item {
      border-bottom: 1px solid #e96fa2;
      &:last-child {
        border: 0;
      }
    }
  }
}

.c-list__title {
  font-weight: normal;
  margin: 0;
  padding: 1rem 2rem .5rem;
  text-align: left;
}

.c-list__content {
  margin: 0;
  padding: 2rem 6rem;
}

.c-list__item {
  padding: 1.5rem 1rem;
  border-bottom: 1px solid #ddb45c;

  &:last-child {
    border: 0;
  }
}
</style>