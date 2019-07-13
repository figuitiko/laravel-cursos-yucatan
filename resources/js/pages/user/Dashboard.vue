<template>
    <div class="container">
        <div class="card card-default">
            <div class="card-header">Dashboard</div>
            <div class="card-body">
                Bienvenue
            </div>
        </div>
        <div class="card-body">
            <taskUser></taskUser>
        </div>
    </div>
</template>
<script>
    import taskUser from '../../components/Tasks-Users.vue'
    export default {

        data() {
            return {

//

            }
        },
        components: {
            taskUser
//

        }
    }
</script>