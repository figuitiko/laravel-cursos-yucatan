<template>
    <div id="main">
        <header id="header">

            <navigationMenu></navigationMenu>
        </header>

        <div id="content">
            <transition name="fade">
                <router-view></router-view>
            </transition>
        </div>

    </div>
</template>
<script>
    import navigationMenu from './components/Menu.vue'
    export default {
        mounted(){
            console.log(this.$auth.user().email );
        },
        data() {
            return {

//

            }
        },
        components: {
            navigationMenu
        }
    }
</script>