<template>
    <div class="ui centered card">
        <div class="content" v-show="!isEditing">
            <div class="header">{{todo.title}}</div>
            <div class="meta">{{todo.project}}</div>
            <div class="extra content">
                <span class="right floated edit icon"  v-on:click="showForm">
                    <i class="edit icon"></i>
                </span>
                <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
                  <i class='trash icon'></i>
                </span>
            </div>
        </div>
        <div class="content" v-show="isEditing">
            <div class="ui form">
                <div class="field">
                    <label for="">Title</label>
                    <input type="text" v-model="todo.title" ref="title" />
                </div>
                <div class="field">
                    <label for="">Project</label>
                    <input type="text" v-model="todo.project" ref="project" />
                </div>
                <div class="ui-two button attached buttons">
                    <button class="ui basic blue button" v-on:click="hideForm">Close X</button>
                </div>
            </div>
        </div>
        <div class="ui bottom attached green basic button" v-show="!isEditing &&todo.done" v-on:click="restoreTodo(todo)">Completed</div>
        <div class="ui bottom attached red basic button" v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">Pending</div>
    </div>
</template>

<script>
    export default {
        props: ['todo'],
        data() {
            return {
                isEditing: false,
            };
        },
        methods: {
            showForm() {
                if (!this.todo.done) {
                    this.isEditing = true;
                }
            },
            hideForm() {
                this.isEditing = false;
            },
            deleteTodo(todo) {
                if (!this.todo.done) {
                    this.$emit('delete-todo', todo);
                }
            },
            completeTodo(todo) {
                this.$emit('complete-todo', todo);
            },
            restoreTodo(todo) {
                this.$emit('restore-todo', todo);
            },
        },
    };
</script>

<style>
    
</style>