<script setup>
import ButtonDelete from './ButtonDelete.vue';

defineProps({todos:{type:Array, require:true}});

</script>

<template>
    <div>
        <h1>Todo List</h1>
        <div class="grid-container" v-if="todos.length > 0">
            <div class="card">
                <div class="card-content" v-for="item of todos" v-bind:key="item.id">
                    <h2>{{ item.todo }}</h2>
                    <ButtonDelete @on-click="$emit('remove', item.ids)">Delete</ButtonDelete>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.grid-container { 
    display: grid;
    grid-template-columns: repeat(auto-fit, minimax(300px, 5fx));
    gap: 8px;
}

.card { 
    border-radius: 8px
}

.card-content { 
    background-color: rgb(226, 226, 183); 
    margin-bottom: 5px;
    padding: 5px 8px;
    width: 200px;
    display: flex;
    justify-content: space-between;
}

h1 {
    margin-bottom: 1rem; 
}

h2 { 
    font-size: 20px;
}

</style>