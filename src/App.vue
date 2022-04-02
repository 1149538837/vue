<template>
  <div id="app">
    <div class="head">
    <nav>
      <router-link to="/">主页</router-link>
      <router-link to="/about">广场</router-link>
      <router-link to="/index">快速匹配</router-link>
    </nav>
    </div>
    <router-view/>

  </div>
</template>


<style lang="scss">
body{
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.head{
background-color: aliceblue;
}
nav {
display: flex;
height: 50px;

  a {
    font-weight: bold;
    color: #2c3e50;
    text-transform: none;
    margin-left: 40px;
    text-align: center;
    line-height: 50px;
    text-decoration: none;

    &.router-link-exact-active {
      color: #42b983;
      text-decoration: none;
      text-align: center;
    }
    &.router-link{
      text-decoration: none;
    }
  }
}
</style>
