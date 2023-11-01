<template>
    <div class="box has-text-weight-bold" :sty;e="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'Box',
        data () {
            return {
                estilo: {
                    'background-color': '#FAF0CA'
                }
            }
        }
    })

</script>
