<template>
    <div>
        <h3>Lista de Usuarios</h3>
        <div class="alert alert-danger" v-if="has_error">
            <p>Imposible de obtener lista de usuarios.</p>
        </div>
        <table class="table">
            <tr>
                <th scope="col">Id</th>
                <th scope="col">nombre</th>
                <th scope="col">description</th>

            </tr>
            <tr v-for="task in tasks" v-bind:key="task.id" style="margin-bottom: 5px;">
                <th scope="row">{{ task.id }}</th>
                <td>{{ task.name }}</td>
                <td>{{ task.description }}</td>
                <td>{{ task.created_at}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                has_error: false,
                tasks: null
            }
        },
        mounted() {
            this.getTasks()
        },
        methods: {
            getTasks() {
                this.$http({
                    url: `tasks/user/${this.$auth.user().id}`,
                    method: 'GET'
                })
                    .then((res) => {
                        console.log(res.data)
                        this.tasks = res.data
                    }, () => {
                        this.has_error = true
                    })
            }
        }
    }
</script>