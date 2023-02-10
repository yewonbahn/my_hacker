//components/ListItem.vue
<template>
  <ol class="list">
    <li v-for="item in listData" v-bind:key="item.id">
      <b>{{ item.time_ago}}</b>
      
      <template v-if="$route.name=='news'">
      <span> by <router-link :to="`/user/${item.user}`">{{ item.user }}</router-link></span><br/>
            <a v-bind:href="item.url">{{ item.title }}</a>
            <router-link v-bind:to="`item?id=${item.id}`"> <i>({{item.comments_count}})</i></router-link>
      </template>
      <template v-else-if="$route.name === 'ask'">
            <span> by <router-link :to="`/user/${item.user}`">{{ item.user }}</router-link></span><br/>
            <router-link v-bind:to="item.url">{{ item.title }}<i>({{item.comments_count}})</i></router-link>
            <!-- a 링크는 페이지를 새로고치므로 현재상태가 리셋된다. 그래서 <router-link></router-link>를 사용한다. -->
      </template>
      <template v-else>
      <span> by {{ item.user }}</span><br/>
            <a v-bind:href="item.url">{{ item.title }}></a>
      </template>
    </li>
  </ol>
</template>

<script>
export default {
    props:['listData'], // 각 메뉴별 view파일에서 propList 로 리스트를 받아 올 것이다.
}
</script>

<style>
</style>