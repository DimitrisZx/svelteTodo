<script>
  import { get } from 'svelte/store';
  
  export let item;
  export let todosList;

  function handleClick(e) {
    const currentItemId = e.target.parentNode.id
    todosList.set([...get(todosList).filter(item => item.id !== parseInt(currentItemId))])
  }
</script>


  <div key={item.id} id={item.id} class="todo">
    <h3>{item.title}</h3>
    <div on:click={ e => handleClick(e)} class="btn">X</div>
  </div>


<style>
  .todo {
    border: 1px solid orange;
    border-radius: 8px;
    width: 400px;
    margin: 0 auto;
    text-align: left;
    padding: 8px 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .todo:not(:last-child) {
    margin-bottom: 8px;
  }

  .btn {
    display: flex;
    background: orange;
    color: white;
    font-size: 12px;
    height: 20px;
    width: 20px;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
  }

  .btn:hover {
    background: rgb(206, 115, 3);
    cursor: pointer;
  }
  
</style>