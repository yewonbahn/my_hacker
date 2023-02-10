<template>
<div>
<tool-bar></tool-bar>
<router-view></router-view></div>
</template>


<script>
import ToolBar from "./components/ToolBar.vue"

export default {
  components:{ToolBar}
}
</script>

<style>
.comment_count {font-size: 10px; color:rgb(56, 120, 120)}
body {font-family: 'Playfair Display', serif; font-size:18px; padding:0; margin:0;}
a {color: black; font-weight: 700;}
* {margin:0; padding:0}
li {list-style-type: none; margin: 20px;}
p + p {margin-top:20px}
#app {padding:0 20px}
.content {padding:30px 20px}
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
header .router-link-active {
    color:coral;
    border-bottom:3px solid coral
}

.list li {padding-left:10px; list-style-type: none}
.list li + li {margin-top:20px}
.list li > a {text-decoration: none; font-size:22px}
.list li > b {font-style: normal; font-size:12px; color:#999}
.list li span {font-style: normal; font-weight:700; font-size:12px; color:#999;}
.list li i {font-style: normal; font-size:12px; color:cornflowerblue}

</style>
