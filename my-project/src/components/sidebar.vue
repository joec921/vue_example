<template lang="html">
  <section class="sidebar">
    <div class='content_container'>sidebar content: {{testStr}}</div>
    <div class='content_container'>Obj: {{author.name}}</div>
    <div class='content_container'>Obj: {{author.company}}</div>

    <slot name='line1'></slot>
    <slot name='line2'></slot>
  
    <slot name='line3'  :data="data"></slot>
    <slot name='line4'  :data="data"></slot>


  </section>
</template>
 
<script lang="js">
  export default  {
    name: 'sidebar',
    props: ['testStr','author'],
    mounted() {
      
    },
    data() {
      return {
        data: ['zhangsan','lisi','wanwu','zhaoliu','tianqi','xiaoba']
      }
    },
    methods: {
    
    },
    computed: {
 
    }
}
</script>
 
<style scoped >
 .content_container{
   margin-top:20px; }
</style>