<template>
    <v-app>
        <v-app-bar elevation="0" style="background-color: transparent" app height="80">
            <div :style="$vuetify.breakpoint.mdAndUp?'width: 60px;':'width: 35px;'">
                <v-img src="/img/logo-13.png"></v-img>
            </div>
            <v-spacer />
            <div :style="$vuetify.breakpoint.mdAndUp?'width: 180px;':'width: 120px;'">
                <v-img src="/img/logo-14.png"></v-img>
            </div>
        </v-app-bar>

        <!-- Sizes your content based upon application components -->
        <v-main style="background-color: #000; background-image: url('/img/fondo.png');background-size: contain;">
            <template v-for="text in frases">
                <div class="blob-wrap" :class="text.first_class">
                    <div class="blob font-blink" :style="$vuetify.breakpoint.mdAndUp?'font-size: 1.5em':'font-size: 1em;'" :class="text.second_class">{{text.text}}</div>
                </div>
            </template>
            <!-- Provides the application the proper gutter -->
            <v-container style="margin-top: -50px;">
                <!-- If using vue-router -->
                <router-view></router-view>
            </v-container>
        </v-main>

        <v-footer dark app fixed color="#E24420">
            <v-col
                    class="text-left font-blink py-0"
                    cols="12" md="6"
            >
                {{ new Date().getFullYear() }} <strong>Juguetron. All Rights Reserved.</strong>
            </v-col>
            <v-col cols="12" md="6" class="text-right font-blink py-0">
                <v-btn
                        color="white"
                        text
                        rounded
                        :to="{name: 'Privacidad'}"
                >
                    Aviso de Privacidad
                </v-btn>
            </v-col>
        </v-footer>
    </v-app>
</template>

<script>

    export default {
        name: "Home",
        mixins: [],
        components: {},
        data: () => ({
            drawer: false,
            var: false,
            activeTab: `Home`,
            screen_width: 0,
            frases: [
                {
                    text: '“Chewie ... estamos en casa”',
                    first_class: 'x',
                    second_class: 'y'
                },
                {
                    text: '“Que la fuerza te acompañe”',
                    first_class: 'blob-2 x2',
                    second_class: 'y2'
                },
                {
                    text: '“La capacidad de hablar no te hace inteligente”',
                    first_class: 'blob-3 x3',
                    second_class: 'y3'
                },
                {
                    text: '“Hazlo o no lo hagas, pero no lo intentes”',
                    first_class: 'blob-4 x2',
                    second_class: 'y4'
                },
                {
                    text: '“Caminos a la victoria hay, distintos que aplastar a un enemigo”',
                    first_class: 'blob-5 x2',
                    second_class: 'y5'
                },
                {
                    text: '“Si creer no puedes, es por eso que fallas”',
                    first_class: 'blob-6 x',
                    second_class: 'y6'
                },
                {
                    text: '“Las armas no ganan batallas. Tu mente, poderosa ella es”',
                    first_class: 'blob-7 x2',
                    second_class: 'y7'
                },
                {
                    text: '“Here comes the sun”',
                    first_class: 'blob-8 x2',
                    second_class: 'y8'
                },
                {
                    text: '“All you need is love”',
                    first_class: 'blob-9 x2',
                    second_class: 'y9'
                },
                {
                    text: '“Hey Jude”',
                    first_class: 'blob-10 x2',
                    second_class: 'y10'
                },
                {
                    text: '“Let it be”',
                    first_class: 'blob-11 x2',
                    second_class: 'y11'
                },
                {
                    text: '“The more I see, the less I know for sure”',
                    first_class: 'blob-12 x2',
                    second_class: 'y12'
                },
                {
                    text: '“Yesterday, all my troubles seemed so far away”',
                    first_class: 'blob-13 x',
                    second_class: 'y13'
                },
                {
                    text: '“Across the Universe”',
                    first_class: 'blob-14 x2',
                    second_class: 'y14'
                },
                {
                    text: '“There´s nothing you can do that can´t be done”',
                    first_class: 'blob-15 x2',
                    second_class: 'y5'
                },
                {
                    text: '"El pasado puede doler pero, tal y como yo lo veo, puedes: o huir de él o aprender"',
                    first_class: 'blob-16 x2',
                    second_class: 'y16'
                },
                {
                    text: '"Algunas veces el camino correcto no es el más fácil"',
                    first_class: 'blob-17 x2',
                    second_class: 'y40'
                },
                {
                    text: '"Yo no estoy loco, mi realidad es diferente a la tuya"',
                    first_class: 'blob-19 x2',
                    second_class: 'y41'
                },
                {
                    text: '“Hola amiguitos”',
                    first_class: 'blob-19 x2',
                    second_class: 'y42'
                },
                {
                    text: '“Muska, miska…”',
                    first_class: 'blob-20 x3',
                    second_class: 'y43'
                },
                {
                    text: '“Para ser arquitecto necesitas dos cosas: optimismo y curiosidad”',
                    first_class: 'blob-21 x',
                    second_class: 'y44'
                },
                {
                    text: '"Un edificio tiene dos vidas: La que imagina su creador y la vida que tiene y no siempre',
                    first_class: 'blob-22 x',
                    second_class: 'y45'
                },
                {
                    text: '“son iguales”',
                    first_class: 'blob-23 x4',
                    second_class: 'y46'
                },
                {
                    text: '"La casa debe ser el estuche de la vida, la máquina de la felicidad”',
                    first_class: 'blob-24 x3',
                    second_class: 'y47'
                },
                {
                    text: '“La idea no es vivir para siempre, la idea es crear algo que sí lo haga”',
                    first_class: 'blob-25 x4',
                    second_class: 'y48'
                },
                {
                    text: '“El arte es lo que dejas salir”',
                    first_class: 'blob-26 x2',
                    second_class: 'y49'
                },
                {
                    text: '“Nunca leo, veo las imágenes”',
                    first_class: 'blob-27 x4',
                    second_class: 'y50'
                }
            ]
        }),
        created() {},
        mounted() {
            this.screen_width = window.innerWidth;
        },
        computed: {},
        watch: {},
        methods: {}
    };
</script>
<style>
    .font-blink {
        font-family: "Blinker" !important;
    }
</style>