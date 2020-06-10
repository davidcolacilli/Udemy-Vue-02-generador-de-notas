<template>
    <h1>{{mainTitle || 'Notes'}}</h1>
</template>

<script>
export default {
  name: 'Header',
  props: {
    mainTitle: String
  }
}
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 15px 0;
}
</style>
