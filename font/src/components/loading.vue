<template>
 
</template>
<script>
    import {

        DEFAULTDATA
    } from '../store/action_type'

    import {
        mapActions
    } from "vuex";



    export default {
        name: 'index',
        data() {
            return {}
        },
        mounted() {

            this.headdataFn(this)
        },
        methods: {
            ...mapActions({
                headdataFn: DEFAULTDATA.actions
            })
        }
    }
</script>

<style scoped>
 
    ul {
        font-size: 0.4rem
    }
    
    .mint-loadmore {
        font-size: 0.48rem
    }
</style>