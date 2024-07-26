<template>
    <div class="box has-text-weight-bold" :style="style">
       <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ActivityBox',
    data(){
        return{
            style: { //Controlar estilo pelo javascript
                background: '#FAF0CA',
            }
        }
    }
});
</script>