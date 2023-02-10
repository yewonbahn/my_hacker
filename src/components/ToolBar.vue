<template>
  <header>
    <router-link 
      to="/news" 
      v-bind:class="{active:isNav.isNews}"
      v-on:click.native="setNav()"
    >News</router-link>
    <!-- a클릭 기본 동작을 감지해야 하므로 .native -->
    <!-- vue에서 제공하는 .router-link-active를 쓰지 못하는 이유는 ask상세 페이지의 경우 http://localhost:8080/item?id=24586033 식으로 처리되는데 이때 ask로 시작하지 않기 때문에 작동이 안됨 그래서 로컬 스토리지에 적어두고 직접구현해서 사용하는 것임. --->
    <router-link 
      to="/ask"
      v-bind:class="{active:isNav.isAsk}"
      v-on:click.native="setNav()"
    >Ask</router-link>
    <router-link 
      to="/jobs"
      v-bind:class="{active:isNav.isJobs}"
      v-on:click.native="setNav()"
    >Jobs</router-link>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isNav: {
        isNews:true, // 기본은 news로 정해둠 
        isAsk:false,
        isJobs:false
      }
    }
  },
  methods : {
    setNav() {
      let currentName = localStorage.getItem('nav');
      let uppCrrName = currentName.charAt(0).toUpperCase() + currentName.slice(1);
      // data의 상태 이름을 처리하기 위해 대문자로 수정
      for ( let item in this.isNav ) { // isNav를 훓트면서 
        if (item === `is${uppCrrName}`) { // 현재 로컬스토리지에 기록된 상태이름과 같은 곳에서
          this.isNav[item] = true;  // true
        } else {
          this.isNav[item] = false; // 아니면 false
        }
      }
    }
  }
}
</script>

<style scoped>
header {
  position: relative;
  padding:20px 30px;
	margin-bottom:30px;
  background:black;
  font-size:24px;
  border-bottom:8px solid lime;
}
header h1 {position: absolute; color:white; top:21px; right:30px; font-size:18px;}
header a {color:white; text-decoration: none; padding-bottom:3px; }
header a + a {margin-left:20px}
header .active {
  color:coral;
  border-bottom:3px solid coral
}
</style>