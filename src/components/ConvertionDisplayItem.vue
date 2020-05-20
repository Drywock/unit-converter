<template>
  <li>
    {{ value }} {{ name }}
  </li>
</template>

<script>
  export default {
    props: [
      "name",
      "ratio",
      "input"
    ],
    computed: {
      value() {
        return this.input * this.ratio ;
      }
    }
  }
</script>