<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="running">
        <span class="icon">
            <i class="fas fa-play"></i>
        </span>
        <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!running">
        <span class="icon">
            <i class="fas fa-stop"></i>
        </span>
        <span>stop</span>
    </button>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Cronometro from './Cronometro.vue';

    export default defineComponent({
        name: 'Temporizador',
        emits: ['aoTemporizadorFinalizado'],
        components: {
            Cronometro
        },
        data() {
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                running: false
            }
        },
        methods: {
            iniciar() {
                if (this.running) return;
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos++;
                }, 1000);
                this.running = true;
            },
            finalizar() {
                clearInterval(this.cronometro);
                this.running = false;
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
                this.tempoEmSegundos = 0;
            }
        }
    });
</script>