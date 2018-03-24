<template>
  <div id="translate-output">
    <h2>{{translatedText}}</h2>
  </div>
</template>

<script>

export default {
  name: 'translate-output',
  props: [
    'translatedText'
  ]
}
</script>

<style>
  #translate-output {
    color: #5dff1a;
    font-size: 40px;
  }
</style>
