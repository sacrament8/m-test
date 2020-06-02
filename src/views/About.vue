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
    function phoneNumberValidate(str, errorSelectorId) {
      const phoneNumber = str.replace(/[━.*‐.*―.*－.*\-.*ー.]/gi, '')
      const pattern = /^(0[5-9]0[0-9]{8}|0[1-9][1-9][0-9]{7})$/
      if (phoneNumber.match(pattern) === null) {
        // 電話番号用正規表現に引っかかったらエラーメッセージを表示
        $(errorSelectorId).show()
      } else {
        $(errorSelectorId).hide()
      }
      // 全部文字列消したらエラーメッセージ消す
      if (phoneNumber === '') {
        $(errorSelectorId).hide()
      }
    }
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
        const inputValue = $(`#input-${i}`).val()
        phoneNumberValidate(inputValue, `#error-${i}`)
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
