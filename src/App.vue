<script>
export default {
    data() {
        return {
            task: '',
            tasks: [],
            error: '',
        }
    },
    methods: {
        addTask() {
            this.error = '';

            if(this.validate(this.task)) {
                this.tasks.push({
                    id: new Date().valueOf(),
                    label: this.task,
                    done: false,
                });
                this.task = '';
            } else {
                this.error = 'Please enter the task.';
            }
        },
        editTask(taskId) {
            let taskIndex = this.tasks.findIndex(task => task.id === taskId);

            this.tasks[taskIndex].done = !this.tasks[taskIndex].done;
        },
        deleteTask(taskId) {
            this.tasks.splice(this.tasks.findIndex(task => task.id === taskId), 1)
        },
        validate(task) {
            return task.length > 0;
        },
    },
}
</script>

<template>
<div>
    <div class="row mb-3">
        <div class="col col-xl-8 offset-xl-2">

            <h1>Todo</h1>

        </div>
    </div>

    <div class="row d-flex justify-content-center">
        <div class="col col-xl-8">

            <div class="card">
                <div class="card-body p-5">

                    <form class="d-flex mb-1">
                        <input @keydown.enter="addTask" v-model="task" type="text" class="form-control me-2" :class="{ 'is-invalid': error.length }" placeholder="New task..." />
                        <button type="submit" disabled class="d-none">Prevent form submit from enter</button>
                        <button @click.prevent="addTask" class="btn btn-primary"><i class="fas fa-plus"></i></button>
                    </form>

                    <div v-show="error.length > 0">
                        <span class="text-danger">{{ error }}</span>
                    </div>

                    <div class="d-flex align-items-center mt-4">
                        <h4 class="flex-fill m-0">Tasks</h4>
                    </div>

                    <div v-show="tasks.length > 0" class="list-group mt-3">
                        <div v-for="task in tasks" class="list-group-item list-group-item-action d-flex align-items-center">
                            <a @:click.prevent="editTask(task.id)" class="btn btn-sm me-2" :class="[task.done ? 'btn-outline-success' : 'btn-outline-secondary']">
                                <i class="fas fa-check" :class="{ 'text-white': !task.done }"></i>
                            </a>

                            <p class="flex-grow-1 mb-0 text-secondary" :class="{ 'text-decoration-line-through': task.done }">{{ task.label }}</p>

                            <a @:click.prevent="deleteTask(task.id)" class="btn btn-sm text-danger">
                                <i class="fas fa-trash"></i>
                            </a>
                        </div>
                    </div>

                    <p v-show="tasks.length == 0" class="mt-4 text-center">Hooray! You don't have any task.</p>

                </div>
            </div>

        </div>
    </div>

    <div class="row mt-3">
        <div class="col col-xl-8 offset-xl-2 text-end">

            <span>Made with <a href="https://vuejs.org" target="_blank">Vue.js</a></span>

        </div>
    </div>
</div>
</template>
