<template>
  <div id="app">    
    <HelloWorld />
    <custom-component></custom-component>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  beforeMount() {
    // add reference to web component js file
    const componentScriptID = 'customComponent';
    if (!document.getElementById(componentScriptID)) {
      const componentScript = document.createElement('script');
      componentScript.setAttribute('id', componentScriptID);
      componentScript.setAttribute(
        'src',
        `//localhost:8888/custom-component.js`
      );
      componentScript.async = true;
      document.head.appendChild(componentScript);
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;  
  color: #2c3e50;  
}
</style>
