<template>
  <div class="container">
    <ul class="list"></ul>
  </div>
</template>

<script>
import $ from 'jquery'
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  mounted() {
    for (let i = 0; i < 300; i++) {
      $('.list').append(
        `<li class="item" id="item-${i}">${i}番目のリスト要素</li>`
      )
      $(`#item-${i}`).on('click', function() {
        console.log(`私は${i}番目のリスト要素です`)
        alert(
          `私が死んでも代わりはいるものと${i}番目の綾波レイが申しております`
        )
        $(`#item-${i}`).text('クリックされたよ!!!')
      })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
h3 {
  margin: 40px 0 0;
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
.container {
  width: 100%;
}
.list {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  height: auto;
}
.list > .item {
  display: block;
  cursor: pointer;
  margin-bottom: 10px;
  width: 300px;
  color: white;
  padding: 8px;
  border-radius: 5px;
  background-color: darkblue;
}
</style>
