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

<!-- * 2.0 Импортируем только что созданный компонент [src\components\BigYellowUsername.vue], а также регистрируем его локально в опции "components". -->
<script>
import { defineAsyncComponent } from 'vue'

// import BigYellowUsername from './BigYellowUsername.vue'

// 4.3.1 В секции "data" создадим эту реф-переменную "showUsername" и поставим ей значением false. ↑
// 4.4 Теперь нам уже не обязательно загружать этот комп. BigYellowUsername, т.к. он отображается лишь по нажатию кнопки. Мы можем удалить обычный импорт и использовать тот же динамический метод загрузки комп., что мы видели в [src\router\index.js].
// 4.5 Во Vue 2 этого было бы достаточно, но во Vue 3, т.к. функциональные комп. определены как чистые функции, описание асинхронных функциональных компонентов должны быть отдельно определены. Нам нужно обернуть это в специальную функцию-помощник defineAsyncComponent.
// 4.6 Также, если мы хотим определить для нашего кусочка асинхронно подгружаемого кода/"чанка" название, то сделать это можно в специальном комментарии внутри импорта перед путём к компоненту. Вот и всё, теперь браузер будет загружать этот компонент только тогда, когда этот компонент потребуется отобразить и закэширует его для будущего отображения.
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
