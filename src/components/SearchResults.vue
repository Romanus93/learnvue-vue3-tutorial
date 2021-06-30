<template>
  <div class="root">
    <!-- <pre>
      {{titlesArray}}
    </pre> -->
    <h2> Showing {{ filteredTitles.length }} results for "{{ query }}"</h2>
    <ul>
      <li v-for="title in filteredTitles" :key="title.page" >
        {{title.Name}}
      </li>
    </ul>
  </div>
</template>

<script>
import titles from '../post-data.json'
import { computed , onBeforeUpdate } from 'vue';

export default {
  props: {
    query: String
  },
  setup(props, context) {
    
    const filteredTitles = computed(() => {
      return titles.filter(s => s.Name.toLowerCase().includes(props.query))
    });

    const consoleFunc = function () {
      console.log('console fuc');
    };

    const titlesArray = titles;

    // const objTitles = reactive(titles);
    console.log(props.query);
    console.log(titles.length);
    console.log(`props query ${props.query}`)
    console.log(`titles ${titles}`);

    // hook 호출
    onBeforeUpdate(()=> {
      console.log(`props.query ${props.query}`);
    });

    return {
      filteredTitles,
      consoleFunc,
      titlesArray
      // objTitles
    }
  },
}
</script>

<style scoped>
  .root {
    width: 400px;
    margin: 0 auto;
  }

  .root p {
    text-align: right;
    font-size: 0.7em;
    margin: 0;
  }

  ul {
    list-style: none;
    width: 50px 0;
  	padding: 0;
		background-color: #fafafa;
		border-radius: 5px;
		border: 1px solid #ddd;
	}

	li {
		text-align: left;
		padding: 20px;
		border-bottom: 1px solid #ddd;
	}
  
	li:nth-last-of-type(1) {
		border-bottom: none;
	}
</style>