<template>
  <div>
    <h1>{{ title }}</h1>
    <router-view>
    <ul>
      <li v-for="item of items" :key='item.id'>
        <input type="checkbox" v-model="item.completed">
        {{ item.text }}
      </li>
    </ul>
    <form @submit.prevent = 'addItem'>
      <input type="text" v-model="newItem" placeholder="Add new Item">
      <button type="submit">Add</button>
    </form>
  </router-view>
  </div>
</template>

<script>
export default {
  data(){
    return{
      title: 'ToDo List',
      items : [
        {id:1, text: 'Learn Vue', completed:false},
        {id:2, text:'Build An App', completed:true}
      ],
      newItem:'',
    }
  },
  methods:{
    addItem(){
      if(this.newItem.trim() !== ''){
        this.items.push({
          id:Date.now(),
          text:this.newItem.trim(),
          completed:false,
        });
        this.newItem='';
      }
    },
  },
};
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
