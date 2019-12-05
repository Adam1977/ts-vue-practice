<template>
  <div class="hello">
    <p>{{msg}}</p>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  // 第一种
  // export default Vue.extend({
  //   data () {
  //     return {
  //       msg: 123123
  //     }
  //   },
  //   created() {
  //     this.testTs('123')
  //   },
  //   methods: {
  //     testTs(par: number) {
  //       console.log(par)
  //     }
  //   }
  // })

  // 第二种
  import Component from 'vue-class-component'
  @Component
  export default class App extends Vue {
    msg = 1233333
    created() {
      App.test('123')
      console.log(11111)
    }
    mounted() {
      App.test('3333')
      console.log(2222)
    }
    static test(par: string){
      console.log(par)
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.hello {
  p {
    background: #ccc;
    color: red;
  }
}
</style>
