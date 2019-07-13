<template>
<!--    <div class="container">-->
<!--        <div class="card card-default">-->
<!--            <div class="card-header">Connexion</div>-->
<!--            <div class="card-body">-->
<!--                <div class="alert alert-danger" v-if="has_error">-->
<!--                    <p>Erreur, impossible de se connecter avec ces identifiants.</p>-->
<!--                </div>-->
<!--                <form autocomplete="off" @submit.prevent="login" method="post">-->
<!--                    <div class="form-group">-->
<!--                        <label for="email">E-mail</label>-->
<!--                        <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email" required>-->
<!--                    </div>-->
<!--                    <div class="form-group">-->
<!--                        <label for="password">Mot de passe</label>-->
<!--                        <input type="password" id="password" class="form-control" v-model="password" required>-->
<!--                    </div>-->
<!--                    <button type="submit" class="btn btn-default">Connexion</button>-->
<!--                </form>-->
<!--            </div>-->
<!--        </div>-->

        <div class="container-fluid">
            <div class="row no-gutter">
                <div class="d-none d-md-flex col-md-4 col-lg-6 bg-image"></div>
                <div class="col-md-8 col-lg-6">
                    <div class="login d-flex align-items-center py-5">
                        <div class="container">
                            <div class="row">
                                <div class="col-md-9 col-lg-8 mx-auto">
                                    <h3 class="login-heading mb-4">Welcome back!</h3>
                                    <div class="alert alert-danger" v-if="has_error">
                                        <p>Erreur, impossible de se connecter avec ces identifiants.</p>
                                    </div>
                                    <form autocomplete="off" @submit.prevent="login" method="post">
                                        <div class="form-group">
                                            <label for="email">E-mail</label>
                                            <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email" required>
                                        </div>
                                        <div class="form-group">
                                            <label for="password">Mot de passe</label>
                                            <input type="password" id="password" class="form-control" v-model="password" required>
                                        </div>
                                        <button type="submit" class="btn btn-lg btn-primary btn-block btn-login text-uppercase font-weight-bold mb-2">Connexion</button>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

<!--    </div>-->
</template>
<script>
    export default {
        data() {
            return {
                email: null,
                password: null,
                has_error: false
            }
        },
        mounted() {

//

        },
        methods: {
            login() {

// get the redirect object

                var redirect = this.$auth.redirect()
                var app = this
                this.$auth.login({
                    params: {
                        email: app.email,
                        password: app.password
                    },
                    success: function() {

// handle redirection

                        // const redirectTo = redirect ? redirect.from.name : this.$auth.user().role === 2 ? 'admin.dashboard' : 'dashboard'+ ','+`params: { id: ${app.$auth.user().id} }`
                        // this.$router.push({name: redirectTo})

                        if(redirect){
                            redirect.from.name
                        }
                         else if(this.$auth.user().role === 2){
                             this.$router.push({name:'admin.dashboard'})
                         }
                         else{
                            this.$router.push({name:'dashboard', params:{ id: app.$auth.user().id }})
                        }
                    },
                    error: function() {
                        app.has_error = true
                    },
                    rememberMe: true,
                    fetchUser: true
                })
            }
        }
    }
</script>