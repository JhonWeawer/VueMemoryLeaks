<template>
  <div>
    <button 
      id="test" 
      @click="myMetd"
    >
      Button that causes memory leaks
    </button>

    <div v-for="item in 1000" v-bind:key="item">
      <MyComponent />
    </div>
  </div>
</template>

<script>
import MyComponent from './MyComponent.vue';

export default {
  name: 'App',
  components: {
    MyComponent
  },
  methods: {
    myMetd() {
      console.log('hi from method :)');
    },
  },
  mounted() {
    // document.getElementById('test').addEventListener('click',this.myMetd);
    console.log('mounted')
  },
  beforeUnmount() {
    // document.getElementById('test').removeEventListener('click',this.myMetd);
    console.log('destroyed');
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
