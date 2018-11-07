<template>
    <div class="container">
        <app-header></app-header>
        <div class="row">
            <div class="col-xs-12">
                <transition name="slide" mode="out-in">
                    <router-view></router-view>
                </transition>
            </div>
        </div>
    </div>
</template>

<script>
    import Header from './components/Header.vue';

    export default {
        components: {
            appHeader: Header
        },
        created() {
            this.$store.dispatch('initStocks');
        }
    }
</script>

<style>
    body {
        padding: 30px;
    }

    .slide-enter-active {
        -webkit-animation: slide-in 200ms ease-out forwards;
        -o-animation: slide-in 200ms ease-out forwards;
        animation: slide-in 200ms ease-out forwards;
    }

    .slide-leave-active {
        -webkit-animation: slide-out 200ms ease-out forwards;
        -o-animation: slide-out 200ms ease-out forwards;
        animation: slide-out 200ms ease-out forwards;
    }

    @keyframes slide-in {
        from {
            -webkit-transform: translateY(-30px);
            -moz-transform: translateY(-30px);
            -ms-transform: translateY(-30px);
            -o-transform: translateY(-30px);
            transform: translateY(-30px);
            opacity: 0;
        }
        to {
            -webkit-transform: translateY(0);
            -moz-transform: translateY(0);
            -ms-transform: translateY(0);
            -o-transform: translateY(0);
            transform: translateY(0);
            opacity: 1;
        }
    }

    @keyframes slide-out {
        from {
            -webkit-transform: translateY(0);
            -moz-transform: translateY(0);
            -ms-transform: translateY(0);
            -o-transform: translateY(0);
            transform: translateY(0);
            opacity: 1;
        }
        to {
            -webkit-transform: translateY(-30px);
            -moz-transform: translateY(-30px);
            -ms-transform: translateY(-30px);
            -o-transform: translateY(-30px);
            transform: translateY(-30px);
            opacity: 0;
        }
    }
</style>
