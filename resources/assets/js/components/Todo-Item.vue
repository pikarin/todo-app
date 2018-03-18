<template>
    <div class="mb-4">
        <div class="flex item-center w-full" v-show="state.edit === false">
            <input type="checkbox" class="mr-2" v-model="data.finished" @click="updateTodo">

            <p class="w-auto"
                :class="data.finished ? 'line-through text-green' : 'text-grey-darkest cursor-pointer hover:text-black hover:font-bold' "
                @click="startEdit"
                v-text="todo.text"
            ></p>

            <button @click="remove(index)"
                class="flex-no-shrink p-2 ml-auto border-2 rounded text-red border-red hover:text-white hover:bg-red"
            >
                Remove
            </button>
        </div>
        
        <div class="flex items-center w-full" v-show="state.edit === true">
            <input type="text" v-model="data.text" @keyup.enter="updateTodo"
                class="appearance-none border rounded w-full py-2 px-3 mr-2 text-black"
                placeholder="Update Todo" 
            >

            <button @click="updateTodo" :disabled="data.text.length === 0"
                class="flex-no-shrink p-2 ml-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal"
            >
                Update
            </button>

            <button @click="cancelEdit"
                class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red"
            >
                Cancel
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['todo', 'index'],

        data() {
            return {
                state: {
                    edit: false,
                },
                data: {
                    text: '',
                    finished: false,
                }
            }
        },

        mounted() {
            const t = this

            t.data.text = t.todo.text
            t.data.finished = t.todo.finished
        },

        methods: {
            updateTodo() {
                const t = this

                t.$nextTick(() => {
                    Bus.$emit('update-todo', {data: t.data, index: t.index, id: t.todo.id})
                })

                t.state.edit = false
            },

            remove() {
                const t = this

                Bus.$emit('remove-todo', {index: t.index, id: t.todo.id})
            },

            startEdit() {
                const t = this

                if (t.data.finished === false) {
                    t.state.edit = true
                }
            },

            cancelEdit() {
                const t = this

                t.state.edit = false
                t.data.text = t.todo.text
            }
        }
    }
</script>