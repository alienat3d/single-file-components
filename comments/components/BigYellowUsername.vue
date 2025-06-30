<script>
// * 1.0 Опишем проп для этого комп. с помощью "Options API"
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

<!-- * 3.0 Чтобы воспользоваться преимуществами CSS-препроцессоров нам нужно сперва установить sass-loader (npm i -D sass-loader --force) -->
<style lang="scss">
$size: 50pt;
$yellow: #DCAE1D;

.username{
  font-size: $size;
  color: $yellow;
}
</style>
