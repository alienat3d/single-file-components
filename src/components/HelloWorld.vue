<template>
  <div class="hello">
    <!-- 4.3.2 Ну, а ещё нам нужна кнопка, которая будет переключать значение showUsername с false на true и обратно. ↓ -->
    <button @click="showUsername = !showUsername">Show/Hide My Name!</button>
    <!-- 2.1 Теперь мы можем использовать его в шаблоне. -->
    <!-- 4.3.0 Мы можем импортировать не только View-компоненты страниц, но и другие компоненты. Чтобы продемонстрировать обернём комп. BigYellowUsername в div и будем показывать его по условию, что showUsername в значении "true". ↓ -->
    <div v-if="showUsername">
      <BigYellowUsername username="alienat3d" />
    </div>
  </div>
</template>

<script>
import { defineAsyncComponent } from 'vue'

export default {
  name: 'HelloWorld',
  components: {
    BigYellowUsername: defineAsyncComponent(() => import(/* webpackChunkName: "BigYellowUsername" */'./BigYellowUsername.vue'))
  },
  props: {
    msg: String
  },
  data () {
    return {
      showUsername: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
