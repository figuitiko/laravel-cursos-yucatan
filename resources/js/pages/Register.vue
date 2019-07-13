<template>

<!--        <div class="card card-default">-->
<!--            <div class="card-header">Inscription</div>-->
<!--            <div class="card-body">-->
<!--                <div class="alert alert-danger" v-if="has_error && !success">-->
<!--                    <p v-if="error == 'registration_validation_error'">Error(s) consulte los mensajes abajo</p>-->
<!--                    <p v-else>Error imposible conectarse ahora.</p>-->
<!--                </div>-->
<!--                <form autocomplete="off" @submit.prevent="register" v-if="!success" method="post">-->
<!--                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.email }">-->
<!--                        <label for="email">E-mail</label>-->
<!--                        <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email">-->
<!--                        <span class="help-block" v-if="has_error && errors.email">{{ errors.email }}</span>-->
<!--                    </div>-->
<!--                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">-->
<!--                        <label for="password">Contraseña</label>-->
<!--                        <input type="password" id="password" class="form-control" v-model="password">-->
<!--                        <span class="help-block" v-if="has_error && errors.password">{{ errors.password }}</span>-->
<!--                    </div>-->
<!--                    <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">-->
<!--                        <label for="password_confirmation">Confirmation mot de passe</label>-->
<!--                        <input type="password" id="password_confirmation" class="form-control" v-model="password_confirmation">-->
<!--                    </div>-->
<!--                    <button type="submit" class="btn btn-default">Inscription</button>-->
<!--                </form>-->
<!--            </div>-->
<!--        </div>-->

        <div class="container-fluid">
            <div class="row no-gutter">
                <div class="d-none d-md-flex col-md-4 col-lg-6 bg-image"><h1>curso yucatan</h1></div>
                <div class="col-md-8 col-lg-6">
                    <div class="login d-flex align-items-center py-5">
                        <div class="container">
                            <div class="row">
                                <div class="col-md-9 col-lg-8 mx-auto">
                                    <h3 class="login-heading mb-4">Registrate aqui</h3>
                                    <div class="alert alert-danger" v-if="has_error && !success">
                                        <p v-if="error == 'registration_validation_error'">Error(s) consulte los mensajes abajo</p>
                                        <p v-else>Error imposible conectarse ahora.</p>
                                    </div>
                                    <form autocomplete="off" @submit.prevent="register" v-if="!success" method="post">
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.name }">
                                            <label for="username">Nombre Completo</label>
                                            <input type="text" id="username" class="form-control" placeholder="Nombre Completo" v-model="name">
                                            <span class="help-block" v-if="has_error && errors.name">{{ errors.name }}</span>
                                        </div>
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.email }">
                                            <label for="email">E-mail</label>
                                            <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email">
                                            <span class="help-block" v-if="has_error && errors.email">{{ errors.email }}</span>
                                        </div>
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.phone }">
                                            <label for="phone">Teléfono</label>
                                            <input type="text" id="phone" class="form-control" placeholder="Teléfono" v-model="phone">
                                            <span class="help-block" v-if="has_error && errors.phone">{{ errors.phone }}</span>
                                        </div>
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.institution }">
                                            <label for="institution">Institución</label>
                                            <input type="text" id="institution" class="form-control" placeholder="Institución" v-model="institution">
                                            <span class="help-block" v-if="has_error && errors.institution">{{ errors.institution }}</span>
                                        </div>
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">
                                            <label for="password">Contraseña</label>
                                            <input type="password" id="password" class="form-control" v-model="password">
                                            <span class="help-block" v-if="has_error && errors.password">{{ errors.password }}</span>
                                        </div>
                                        <div class="form-group" v-bind:class="{ 'has-error': has_error && errors.password }">
                                            <label for="password_confirmation">Confirmacion de Contraseña</label>
                                            <input type="password" id="password_confirmation" class="form-control" v-model="password_confirmation">
                                        </div>
                                        <button type="submit" class="btn btn-lg btn-primary btn-block btn-login text-uppercase font-weight-bold mb-2">Inscription</button>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>



</template>
<script>
    export default {
        data() {
            return {
                name: '',
                email: '',
                password: '',
                phone: '',
                institution:'',
                password_confirmation: '',
                has_error: false,
                error: '',
                errors: {},
                success: false
            }
        },
        methods: {
            register() {
                var app = this
                this.$auth.register({
                    data: {
                        name: app.name,
                        email: app.email,
                        phone: app.phone,
                        institution: app.institution,
                        password: app.password,
                        password_confirmation: app.password_confirmation
                    },
                    success: function () {
                        app.success = true
                        this.$router.push({name: 'login', params: {successRegistrationRedirect: true}})
                    },
                    error: function (res) {
                        console.log(res.response.data.errors)
                        app.has_error = true
                        app.error = res.response.data.error
                        app.errors = res.response.data.errors || {}
                    }
                })
            }
        }
    }
</script>
<style scoped>

</style>