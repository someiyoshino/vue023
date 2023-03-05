<script setup>
import { ref } from 'vue';
import { useTodoList } from '/src/composables/useTodoList.js';

// const todoListRef = ref([]);
// const ls = localStorage.todoList;
// todoListRef.value = ls ? JSON.parse(ls) : [];
// const todoExample = ref(['example1', 'example2', 'example3']);
const todoRef = ref('');
const isEditRef = ref(false);
// let editId = -1;
const { todoListRef, add, show, edit, del, check } = useTodoList();

const addTodo = () => {
    // const id = new Date().getTime();
    // todoListRef.value.push({ id: id, task: todoRef.value });
    // console.log(todoRef.value);
    // localStorage.todoList = todoRef.value;
    // localStorage.todoList = JSON.stringify(todoListRef.value);
    // console.log(localStorage.todoList);
    // console.log(todoListRef.value);
    add(todoRef.value);
    todoRef.value = '';
};

const showTodo = (id) => {
    // const todo = todoListRef.value.find((todo) => todo.id === id);
    // todoRef.value = todo.task;
    // editId = id;
    todoRef.value = show(id);
    isEditRef.value = true;
};

const editTodo = () => {
    // const todo = todoListRef.value.find((todo) => todo.id === editId);
    // const idx = todoListRef.value.findIndex((todo) => todo.id === editId);
    // todo.task = todoRef.value;
    // todoListRef.value.splice(idx, 1, todo);
    // localStorage.todoList = JSON.stringify(todoListRef.value);
    // editId = -1;
    edit(todoRef.value);
    isEditRef.value = false;
    todoRef.value = '';
};

const deleteTodo = (id) => {
    // const todo = todoListRef.value.find((todo) => todo.id === id);
    // const idx = todoListRef.value.findIndex((todo) => todo.id === id);
    // const { todo, idx } = useTodoList(id);
    // const delMsg = '「' + todo.task + '」を削除しますか？';
    // if (!confirm(delMsg)) return;
    // todoListRef.value.splice(idx, 1);
    // localStorage.todoList = JSON.stringify(todoListRef.value);
    del(id);
};

const changeCheck = (id) => {
    check(id);
};
</script>

<template>
    <!-- input -->
    <div class="box_input">
        <input type="text" class="todo_input" v-model="todoRef" placeholder="+ TODOを入力" />
        <!-- <button class="btn" @click="addTodo">add</button> -->
        <button class="btn green" @click="editTodo" v-if="isEditRef">変更</button>
        <button class="btn" @click="addTodo" v-else>追加</button>
    </div>

    <!-- list -->
    <div class="box_list">
        <div class="todo_list" v-for="todo in todoListRef" :key="todo.id">
            <div class="todo">
                <input type="checkbox" class="check" /><label>{{ todo.task }}</label>
            </div>
            <div class="btns">
                <button class="btn green" @click="showTodo(todo.id)">編</button>
                <button class="btn pink" @click="deleteTodo(todo.id)">削</button>
            </div>
        </div>
    </div>
</template>

<style sacoped>
.box_input {
    margin-top: 20px;
}

.todo_input {
    width: 300px;
    margin-right: 8px;
    padding: 8px;
    font-size: 18px;
    border: 1px solid #aaa;
    border-radius: 6px;
}

.btn {
    padding: 8px;
    background-color: #03a9f4;
    border-radius: 6px;
    color: #fff;
    text-align: center;
    font-size: 14px;
}

.box_list {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.todo_list {
    display: flex;
    align-items: center;
    gap: 8px;
}

.todo {
    border: 1px solid #ccc;
    border-radius: 6px;
    padding: 12px;
    width: 300px;
}

.check {
    border: 1px solid red;
    transform: scale(1.6);
    margin: 0 16px 2px 6px;
    /* width: 10px; */
    /* height: 10px; */
    /* appearance: auto; */
}

.btns {
    display: flex;
    gap: 4px;
}

.green {
    background-color: #00c853;
}

.pink {
    background-color: #ff4091;
}
</style>
