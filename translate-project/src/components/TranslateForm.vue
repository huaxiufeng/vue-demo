<template>
  <div class="row" id="translate-form">
    <div class="col-md-6 col-md-offset-3">
      <form id="translate-form-body" class="well form-inline" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容"/>
        <select class="form-control" v-model="lang">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Japanese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译"/>
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'translate-form',
  data: function () {
    return {
      textToTranslate: '',
      lang: ''
    }
  },
  methods: {
    formSubmit: function (e) {
      // 子组件向父组件传递事件和参数，使用emit，第一个参数是事件的名称，不是方法
      this.$emit('textSubmit', this.textToTranslate, this.lang)
      e.preventDefault()
    }
  },
  created: function () {
    this.lang = 'en'
  }
}
</script>

<style>
  #translate-form-body {
    border: 1px solid #ccc;
    border-radius: 10px;
  }
</style>
