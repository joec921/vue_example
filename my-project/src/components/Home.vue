<template lang="html">
  <section class="home">
    <h1>home Component</h1>
    {{homeVar}}
     <button class="button" v-on:click="getFromParnet()">Change Message</button>
     <button class="button" v-on:click="changeValue()">Change component value</button>
    <sidebar v-bind:testStr="this.vnum"  v-bind:author="{ name: 'Veronica', company: 'Veridian Dynamics' }">
      <h2 slot='line1'>From parent line1 </h2>
      <h3 slot='line2'>From parnet line2 </h3> 

      <template slot='line3' slot-scope="sidebarData">
        <div class="tmpl">
          <span v-for="item in sidebarData.data">{{item}}</span>
        </div>
      </template>

     <template slot='line4' slot-scope="sidebarData">
       <div>{{sidebarData.data}}</div>
      </template>

    </sidebar>

  </section>
</template>
 
<script lang="js">

  import sidebar from './sidebar'

  export default  {
    components:{ 'sidebar' : sidebar},
    name: 'home',
    props: [],
    mounted() {
      
    },
    data() {
      return {
        homeVar: this.$parent.test1,
        vnum : 0
      }
    },
    methods: {
            getFromParnet() {
                this.homeVar = 'abc';
            },
                changeValue() {
                this.vnum++
            }        
    },
    computed: {
 
    }
}
</script>
 
<style scoped >
  .home {
 
  }
</style>