<template>
    <div id="app">
        <div class="container">
            <div class="col-md-6 col-md-offset-3">
                <h1 class="text-center">투 두 리스트</h1>
                <input type="text" class="form-control" v-model="todoInput" @keyup.enter="addTodo" />
                <div class="list-group">
                    <template v-for="todo in activeTodoList">
                        <button
                            class="list-group-item text-left"
                            :key="todo.id"
                            @click="toggleTodoState(todo)"
                        >{{ todo.label }}</button>
                    </template>
                </div>

                <div class="text-right">
                    <button class="btn btn-sm" @click="changeCurrentState('active')">할 일</button>
                    <button class="btn btn-sm" @click="changeCurrentState('done')">완료</button>
                    <button class="btn btn-sm" @click="changeCurrentState('all')">전체</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
let id = 0
export default {
    name: 'app',
    data() {
        return {
            todoInput: '',
            todoList: [],
            currentState: 'active'
        }
    },

    computed: {
        activeTodoList() {
            return this.todoList.filter(
                todo =>
                    this.currentState === 'all' ||
                    todo.state === this.currentState
            )
        }
    },
    methods: {
        changeCurrentState(state) {
            this.currentState = state
        },
        addTodo(e) {
            let todo = {
                id: id++,
                label: e.target.value,
                state: 'active'
            }
            this.todoList.push(todo)
            this.todoInput = ''
        },
        toggleTodoState(todo) {
            todo.state = todo.state === 'active' ? 'done' : 'active'
        }
    },
    components: {}
}
</script>

<style>
</style>
