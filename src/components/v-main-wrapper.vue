<template>
  <div class="v-main-wrapper">
    <keep-alive>
      <router-view></router-view>    
    </keep-alive>
  </div>
</template>
<!--Keep alive сохраняет состояние при изменении url-->
<script>

export default {
  name: 'v-main-wrapper',
  props: {},
  data() {
    return {
      title: 'Main Wrapper'
    }
  },
  computed: {},
  methods: {},
  watch: {},
}
</script>

<style>
  .v-main-wrapper{
    max-width: 900px;
    margin: 0 auto;
  }
</style>