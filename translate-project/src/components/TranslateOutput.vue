<template>
  <div id="translate-output">
    <h2>{{result}}</h2>
  </div>
</template>

<script>

export default {
  name: 'translate-output',
  props: {
    result: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
  #translate-output {
    color: #5dff1a;
    font-size: 40px;
  }
</style>
