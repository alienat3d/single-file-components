<script>
export default {
  props: {
    username: {
      type: String,
      required: true
    }
  }
}
</script>

<template>
  <p class="username">{{ username }}</p>
</template>

<style lang="scss">
$size: 50pt;
$yellow: #DCAE1D;

.username{
  font-size: $size;
  color: $yellow;
}
</style>
