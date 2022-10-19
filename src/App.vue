<template>
  <div id="app">
    <navbar />
    <router-view/>
    
  </div>
</template>
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-6305863275081549"
     crossorigin="anonymous"></script>
<ins class="adsbygoogle"
     style="display:block"
     data-ad-format="fluid"
     data-ad-layout-key="-fb+5w+4e-db+86"
     data-ad-client="ca-pub-6305863275081549"
     data-ad-slot="4202572180"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>
<style>
  @import './assets/styles.css';
</style>