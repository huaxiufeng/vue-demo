<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <!-- v-on后面接的是事件的名称，也就是emit的第一个参数 -->
    <translate-form v-on:textSubmit="translateText"></translate-form>
    <!-- v-bind后面接的是子组件的属性名称 -->
    <translate-output v-bind:result="translatedText"></translate-output>
  </div>
</template>

<script>
/**
 * 引入组件需要先import,然后在components里面注册，然后才可以在template里面使用
 */
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data: function () {
    return {
      translatedText: ''
    }
  },
  components: {
    TranslateOutput,
    TranslateForm
  },
  methods: {
    translateText: function (text, lang) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?' +
        'key=trnsl.1.1.20180324T075403Z.c29c7e89770ac570.29cd4de7b72f4f8055da32d95f93b69f79d9d753' +
        '&lang=' + lang +
        '&text=' + text).then((response) => {
        this.translatedText = response.body.text[0]
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
