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
      $('.list').append(`
      <div>
      <div id="error-${i}" class="error-mess">
        固定電話10桁〜携帯電話11桁の数値を入力してください！
      </div>
      <input type="text" class="input" id="input-${i}" />
      </div>
      `)
      $(`#input-${i}`).on('keyup', function() {
        let phoneNumber = String($(`#input-${i}`).val())
        phoneNumber = phoneNumber.replace(/[━.*‐.*―.*－.*\-.*ー.]/gi, '')
        var pattern = /^(0[5-9]0[0-9]{8}|0[1-9][1-9][0-9]{7})$/
        console.log(phoneNumber)
        var flag = phoneNumber.match(pattern)
        if (flag === null) {
          document.querySelector(`#error-${i}`).style.display = 'block'
        } else {
          document.querySelector(`#error-${i}`).style.display = 'none'
        }
        if (phoneNumber === '') {
          if (phoneNumber === '') {
            document.querySelector(`#error-${i}`).style.display = 'none'
          }
        }
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
.error-mess {
  color: red;
  font-weight: bold;
  display: none;
}
.input {
  display: block;
  margin-bottom: 10px;
  margin-right: 5px;
  width: 300px;
  color: black;
  padding: 8px;
  border-radius: 5px;
  border: solid 2px darkcyan;
}
</style>
