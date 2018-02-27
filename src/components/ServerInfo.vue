<template>
    <div class="col-xs-12 col-sm-6">
        <div v-if="show">
            <p>Server status: {{ status }}</p>
            <button @click="changeStatus">Change Status</button>
        </div>
        <p v-else>Server Details are currently not updated</p>
    </div>
</template>
<script>
    import {
        eventBus
    } from '../main.js';
    export default {
        data: function () {
            return {
                show: false,
                index: 0,
                status: ''
            }
        },
        methods: {
            changeStatus(){
                this.status = "Error";
                eventBus.$emit('changeStatus', this.index, this.status);
            }
        },
        created() {
            eventBus.$on('showServerInfo', (serverInfo) => {
                this.show = true;
                this.index = serverInfo.index;
                this.status = serverInfo.status;
            })
        }
    }
</script>