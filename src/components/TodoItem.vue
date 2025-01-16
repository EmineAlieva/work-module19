<script>

export default{
  props : {
    id: {
      type: Number,
      default:0
    },
    text: {
      type: String,
      default:''
    },
    status:''
  },

  data(){
    return{
      checked:''
    }
  },

  methods: {
    sendEvent(id) {
      this.$emit('delete-task', id)
    }
  }
}

</script>

<template>
  <div>
    <li @click="$emit('toggle-task', id, checked)"> 
      <input type="checkbox" @click.stop="$emit('change-status', id, checked)" :checked="status">
      <span :class="{completed: status }"> {{ text }}</span>
      <button @click="sendEvent(id)" class="button">Удалить задачу</button>
    </li>
  </div>
</template>

<style scoped>
  li {
    font-size: 18px;
    color: green;
    border: 1px solid grey;
    border-radius: 10px;
    max-width: 5500px;
    padding: 0.4rem;
    display: flex;
    position: relative;
    cursor: pointer;
  }
  span{
    margin: 0;
  }
  .completed{
    text-decoration: line-through;
    color: grey;
  }
  .button{
    padding: 4px 8px;
    cursor: pointer;
    position: absolute;
    right: 10px;
    border: none;
    border-radius: 5px;
    background: linear-gradient(150deg, rgb(237, 248, 213), rgb(177, 235, 177) 100%);
    color: rgb(82, 82, 82);
  
  }
  button:hover{
    background: linear-gradient(330deg, rgb(237, 248, 213), rgb(184, 228, 206)500%);
  }
  input {
    margin-right: 10px;
  }
</style>
