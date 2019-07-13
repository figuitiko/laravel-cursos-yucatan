<template>
    <div>
<!--    <nav id="nav">-->
<!--        <ul>-->
<!--            &lt;!&ndash;UNLOGGED&ndash;&gt;-->
<!--            <li v-if="!$auth.check()" v-for="(route, key) in routes.unlogged" v-bind:key="route.path">-->
<!--                <router-link  :to="{ name : route.path }" :key="key">-->
<!--                    {{route.name}}-->
<!--                </router-link>-->
<!--            </li>-->
<!--            &lt;!&ndash;LOGGED USER&ndash;&gt;-->
<!--            <li v-if="$auth.check(1)" v-for="(route, key) in routes.user" v-bind:key="route.path">-->
<!--                <router-link  :to="{ name : route.path,  params: { id: $auth.user().id} }" :key="key">-->
<!--                    {{route.name}}-->
<!--                </router-link>-->
<!--            </li>-->
<!--            &lt;!&ndash;LOGGED ADMIN&ndash;&gt;-->
<!--            <li v-if="$auth.check(2)" v-for="(route, key) in routes.admin" v-bind:key="route.path">-->
<!--                <router-link  :to="{ name : route.path }" :key="key">-->
<!--                    {{route.name}}-->
<!--                </router-link>-->
<!--            </li>-->
<!--            &lt;!&ndash;LOGOUT&ndash;&gt;-->
<!--            <li v-if="$auth.check()">-->
<!--                <a href="#" @click.prevent="$auth.logout()">Logout</a>-->
<!--            </li>-->
<!--        </ul>-->
<!--    </nav>-->
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark static-top">
            <div class="container">
                <a class="navbar-brand" href="#">
                    <img src="http://placehold.it/150x50?text=Logo" alt="">
                </a>
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ml-auto">
                        <li class="nav-item" >
                            <a class="nav-link"><router-link  :to="{ name : 'home' }" >
                                Home
                            </router-link></a>
                        </li>

                        <!--UNLOGGED-->
                        <li class="nav-item" v-if="!$auth.check()" v-for="(route, key) in routes.unlogged" v-bind:key="route.path">
                            <a class="nav-link"><router-link  :to="{ name : route.path }" :key="key">
                                {{route.name}}
                            </router-link></a>
                        </li>
                        <!--LOGGED USER-->
                        <li class="nav-item" v-if="$auth.check(1)" v-for="(route, key) in routes.user" v-bind:key="route.path">
                           <a class="nav-link"> <router-link  :to="{ name : route.path,  params: { id: $auth.user().id} }" :key="key">
                                {{route.name}}
                           </router-link></a>
                        </li>
                        <!--LOGGED ADMIN-->
                        <li class="nav-item" v-if="$auth.check(2)" v-for="(route, key) in routes.admin" v-bind:key="route.path">
                            <a class="nav-link"><router-link  :to="{ name : route.path }" :key="key">
                                {{route.name}}
                            </router-link></a>
                        </li>
                        <!--LOGOUT-->
                        <li class="nav-item"  v-if="$auth.check()">
                            <a class="nav-link" href="#" @click.prevent="$auth.logout()">Logout</a>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>

</template>
<script>
    export default {
        data() {
            return {
                routes: {

// UNLOGGED

                    unlogged: [
                        {
                            name: 'Registrarse',
                            path: 'register'
                        },
                        {
                            name: 'Conectarse',
                            path: 'login'
                        }
                    ],
                    // LOGGED USER

                    user: [
                        {
                            name: 'Dashboard',
                            path: 'dashboard'
                        }
                    ],

// LOGGED ADMIN

                    admin: [
                        {
                            name: 'Dashboard',
                            path: 'admin.dashboard'
                        }
                    ]
                }
            }
        },
        mounted() {



        }
    }
</script>