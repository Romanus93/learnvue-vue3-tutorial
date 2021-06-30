<template>
  <div>
    <h2> Filter LearnVue Articles </h2>
    <input
      type='text'
      placeholder='Filter Search'
      v-model='query'
    />
    <br>
    <button type='button' @click='reset'>Reset</button>
    <search-results :query='query' @accepted="hello"/>
  </div>
</template>

<script>
import { ref } from 'vue';
import SearchResults from './SearchResults.vue';

export default {
  components: {
    SearchResults
  },
  //모든 반응 데이터, 계산 된 속성 , 메소드 등을 정의 할 수있는 곳
  setup () {
    const query = ref('');

    const reset = () => {
      query.value = '';
    };

    const hello = () => {
      console.log('hello emit');
    }

    return {
      query,
      reset,
      hello
    };
  }
}
</script>

<style scoped>
  input[type='text'] {
    margin-bottom: 20px;
    padding: 10px;
  }
</style>
