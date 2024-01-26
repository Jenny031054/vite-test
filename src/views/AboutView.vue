<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ text }}
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
<script>
export default{
  data(){
    return {
      text:{},

    }
  },
  mounted(){
    console.log(import.meta.env.VITE_PATH);
    const url = import.meta.env.VITE_PATH
    this.$http.get(url)
    .then((res)=>{
      console.log(res);
      this.text = res.data.results[0]

    })
    .catch((err)=>{
      console.log(err)
    })
  }
}
</script>
