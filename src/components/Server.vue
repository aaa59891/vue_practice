<template>
    <li class="list-group-item" :class="{error: status === 'Error'}" @click="showStatus">
        Server #{{ index }}
    </li>
</template>

<script>
import { eventBus } from '../main.js';
    export default {
        data: function(){
            return {
                status: "Normal"
            };
        },
        props:['index'],
        methods:{
            showStatus(){
                eventBus.$emit('showServerInfo', {index: this.index, status: this.status});
            }
        },
        created(){
            eventBus.$on('changeStatus', (index, status) => {
                if(index !== this.index){
                    return;
                }
                this.status = status;
            })
        }
    };
</script>
<style scoped>
    .error{
        border: 1px solid red;
    }
</style>
