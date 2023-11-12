<script setup>
import {ref} from 'vue';
import { nanoid } from 'nanoid'

 
  const inputValue = ref('');
  const arr = ref([]);
  const submit = ()=>{
    if(inputValue.value !== ''){
      arr.value.push({
        title:inputValue.value,
        id: nanoid()
      });
      inputValue.value = '';
    }
  };
  const deleteItem = (item)=>{
    arr.value.splice(item,1);
  };

</script>

<template>
  <div class="container">
    <div class="wrapper">
      <h1>todo list</h1>
      <form @submit.prevent="submit">
        <input 
        v-model="inputValue" 
        type="text"
        placeholder="type todo">
        <button type="submit">add</button>
      </form>
      <ul>
        <li v-for="task in arr" v-show="arr.length > 0 ? true : false">
         {{ task.title }}
          <font-awesome-icon
           :icon="['fas', 'xmark']"
           class="icon"
           @click="deleteItem(task)"
           />
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
  *{
    margin: 0;
    padding: 0;
    list-style-type: none;
    text-decoration: none;
    box-sizing: border-box;
  }

  .container{
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #b0e4e1;
  }

  .wrapper{
    width: 50%;
    max-width: 450px;
    padding: 20px;
    border-radius: 10px;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    gap: 15px;
    justify-content: center;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.9);
  }

  h1{
    color: #fff;
    text-transform: capitalize;
    font-size: 35px;
  }

  form{
    width: 100%;
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
  }

  input{
    width: 100%;
    padding: 6px 14px;
    border: none;
    font-size: 17px;
    border-radius: 5px;
    border: none;
    outline: none;
  }

  input::placeholder{
    text-transform: capitalize;
  }

  button{
    padding: 8px 22px;
    margin-left: -3309px;
    border: none;
    cursor: pointer;
    text-transform: capitalize;
    border-radius: 0px 5px 5px 0px;
    transition: all .4s ease;
  }

  button:hover{
    background: #000;
    color: #fff;
  }

  ul{
    width: 100%;
    display: flex;
    flex-flow: column nowrap;
    gap: 10px;
    margin-top: 20px;
  }

  li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(0, 0, 0, 0.1);
    padding: 10px;
    border-radius: 5px;
    color: #fff;
  }

  .icon{
    cursor: pointer;
    color: #fff;
  }

  .icon:hover{
    color: #000;
  }
</style>
