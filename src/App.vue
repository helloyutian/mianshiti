<template>
  <div id="app">
    <div class="main">
      <Nav/>
      <router-view/>
    </div>
    <Aside/>
  </div>
</template>

<script>
import Nav  from './components/nav';
import Aside  from './components/aside';

export default {
  components: {
    Aside,
    Nav
  }
}
</script>>
<style lang="less">
@import './assets/var';
h1,h2,h3,h4,h5,p,ul,ol,li,dl,dt,dd,form {
  margin: 0;
  padding: 0;
}
ul,li,ol {
  list-style: none;
}
a, a:link, a:visited, a:hover {
  text-decoration: none;
}
body {
  background-color: #fdebea;
  // background-image: url(./assets/logo.png);
  background-repeat: no-repeat;
  background-position: left bottom;
  margin: 0;
}
.clearfix::after {
  content: '\20';
  display: block;
  overflow: hidden;
  clear: both;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #17253e;
  background: #fefefe;
  width: 1440px;
  margin: 100px auto;
  border-radius: 50px;
  border: 15px solid rgba(255, 77, 86, .2);
  box-shadow: 0 20px 40px rgba(0, 0, 0, .06);
  display: flex;
  align-items: stretch;
  transition: width ease-in .2s .2s;
  @media (max-width: @lgScreen) {
    width: 1100px;
    transition: width ease-in .2s .2s;
  }
  @media (max-width: @mdScreen) {
    width: 820px;
    .main {
      padding: 50px 48px 50px 58px;
    }
  }
  @media (max-width: @smScreen) {
    margin: 50px 0;
    width: 100%;
    box-sizing: border-box;
    // max-width: 700px;
    
  }
   @media (max-width: @xsScreen) {
     margin: 20px 0;
     .main {
        padding: 20px 28px 20px 28px;
      }
   }
}

.main {
  flex: auto;
  width: 100%;
  padding: 50px 68px 50px 78px;
  box-sizing: border-box;
}
.img-fill {
  display: block;
  margin: 0;
  border: none;
  width: 100%;
}
</style>
