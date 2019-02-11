<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '还未获取数据',
      urlDouban:'https://api.douban.com/v2/movie/top250',
      urlCnode:'https://cnodejs.org/api/v1/topics'
    }
  },
  created(){
      this.getData()
  },
  methods: {
    getData() {
      this.$axios.get('/api/v2/movie/top250',
      {params:{
          start:20,
          count:20
        }}).then((response) => {
        console.log(response.data)
        this.msg=JSON.stringify(response.data.start)
      })
    }
  }
  //   async getData() {
  //     try {
  //       this.msg = await this.$axios.get(this.urlDouban)
  //     } catch (e) {
  //       console.log(e.response) // undefined
  //     }
  //   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
