<template>
    <list-item :list-data="list"></list-item>
  </template>
  
  <script>
  import ListItem from '../components/ListItem';
  
  export default {
    components: {ListItem},
    computed: {
      list() {
        return this.$store.state.list;
      }
    },
    created() {
      this.$store.dispatch('FETCH_LIST', 'jobs');
    }
  }
  </script>

<style>

</style>