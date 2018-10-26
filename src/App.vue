<template>
    <div>
        <p v-if="!name">Loadding</p>
        <p v-else>The most popular repo is <a :href="url">{{ name }}</a></p>
    </div>
</template>


<script>
 import axios from 'axios'
 export default {
    data(){
        return {
          name:'',
          url:''
        }
    },
     mounted() {
       const url = 'https://api.github.com/search/repositories?q=r&sort=stars'
    //    this.$http.get(url).then((result)=>{
    //        this.name = result.data.items[0].name
    //        this.url = result.data.items[0].svn_url
    //    },(err)=>{
    //       alert('请求失败')
    //    })
          axios.get(url).then((result)=>{
              this.name = result.data.items[0].name
              this.url = result.data.items[0].svn_url
          }).catch((err)=>{
              console.log('请求失败')
          })
   },
}
</script>

<style>
  .logo{
     opacity: .5;
  }
</style>
