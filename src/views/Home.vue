<template>
    <v-container ref="contentv">
        <transition name="fade">
            <div class="loading" v-if="loading">
                <div class="loading-window">
                    <div class="loading-text">
                        <span class="loading-text-words">L</span>
                        <span class="loading-text-words">O</span>
                        <span class="loading-text-words">A</span>
                        <span class="loading-text-words">D</span>
                        <span class="loading-text-words">I</span>
                        <span class="loading-text-words">N</span>
                        <span class="loading-text-words">G</span>
                        <div class="sk-folding-cube">
                            <div class="sk-cube1 sk-cube"></div>
                            <div class="sk-cube2 sk-cube"></div>
                            <div class="sk-cube4 sk-cube"></div>
                            <div class="sk-cube3 sk-cube"></div>
                        </div>
                    </div>
                </div>
            </div>
        </transition>
        <v-row class="justify-space-around fill-height">
            <v-card
                    class="pa-2 mb-0 pb-0 mx-auto"
                    flat
                    elevation="0"
                    :width="$vuetify.breakpoint.mdAndUp?'70%':'90%'"
                    style="background-color: rgb(0,0,0,.7)"
            >
                <v-card-text class="pa-0 ma-0">
                    <v-row v-if="!showForm && !end">
                        <v-col cols="12">
                            <div class="text-center font-blink white--text font-weight-bold mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 3em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                ¡ALGO INCREÍBLE ESTÁ POR PASAR!</div>
                            <div class="text-center font-blink white--text font-weight-bold mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 2.5em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 1.6em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                ¿Quieres saber qué es?</div>
                            <div v-if="false" class="text-center font-blink white--text mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 1.8em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 1.2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                Regístrate y sé de los primeros en averiguarlo</div>
                        </v-col>
                        <v-col cols="12">
                            <v-card
                                    class="mx-auto"
                                    style="background: rgb(0,0,0,.5)"
                                    dark
                            >
                                <v-card-text class="headline font-weight-bold text-center mb-0">
                                    <v-row>
                                        <v-col cols="12" class="clock-text mb-0 pb-0">
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_DAYS.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_HOURS.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_MINUTES.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_SECONDS.toString().padStart(2,'0')}}</span>
                                        </v-col>
                                        <v-col cols="12" class="clock clock-text mt-0 pt-0" :style="$vuetify.breakpoint.smAndDown?'font-size: .6em':'font-size: .8em'">
                                            DIAS - HORAS - MINUTOS - SEGUNDOS
                                        </v-col>
                                    </v-row>
                                </v-card-text>
                            </v-card>
                        </v-col>
                        <v-col cols="12" class="text-center">
                            <v-btn @click="goSite" large color="#F75028" class="font-blink font-weight-bold title white--text">¡Descúbrelo acá!</v-btn>
                        </v-col>
                    </v-row>
                    <v-row v-if="showForm">
                        <v-col cols="12">
                            <v-card
                                    max-width="900px"
                                    color="transparent"
                                    outlined
                                    class="pa-2 fill-height mx-auto pt-0 mt-0"
                                    :elevation="0"
                            >
                                <v-card-text class="pa-0 ma-0">
                                    <v-form ref="formJoin">
                                        <v-row>
                                            <v-col cols="12" class="ma-0 pa-0">
                                                <div class="text-center font-blink white--text font-weight-bold mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 2em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                                    ¡REGÍSTRATE!</div>
                                            </v-col>
                                            <v-col cols="12" class="mb-0 pb-0">
                                                <v-text-field
                                                        dense dark
                                                        color="#E64620"
                                                        outlined
                                                        :hide-details="
                                      $vuetify.breakpoint.smAndDown
                                    "
                                                        v-model="formJoin.nombre"
                                                        label="Nombre"
                                                        :rules="[rules.required]"
                                                ></v-text-field>
                                            </v-col>
                                            <v-col cols="12" class="mb-0 pb-0">
                                                <v-text-field
                                                        dense dark
                                                        outlined
                                                        :hide-details="
                                      $vuetify.breakpoint.smAndDown
                                    "
                                                        v-model="formJoin.apellido"
                                                        label="Apellidos"
                                                        :rules="[rules.required]"
                                                ></v-text-field>
                                            </v-col>
                                            <v-col cols="12" class="mb-0 pb-0">
                                                <v-text-field
                                                        dense dark
                                                        outlined
                                                        :hide-details="
                                      $vuetify.breakpoint.smAndDown
                                    "
                                                        v-model="formJoin.correo"
                                                        label="E-mail"
                                                        :rules="[rules.required, rules.email]"
                                                ></v-text-field>
                                            </v-col>
                                            <v-col cols="12" class="mb-0 pb-0">
                                                <v-dialog
                                                        ref="dialog"
                                                        v-model="modalFn"
                                                        persistent
                                                        width="290px"
                                                >
                                                    <template v-slot:activator="{ on }">
                                                        <v-text-field
                                                                dense dark
                                                                outlined
                                                                :hide-details="
                                          $vuetify.breakpoint.smAndDown
                                        "
                                                                v-model="computedDateFormatted"
                                                                label="Tu cumpleaños"
                                                                hint="Día / Mes / Año"
                                                                persistent-hint
                                                                readonly
                                                                v-on="on"
                                                                :rules="[rules.required]"
                                                        ></v-text-field>
                                                    </template>
                                                    <v-date-picker
                                                            ref="picker"
                                                            v-model="formJoin.fechaNacimiento"
                                                            :max="
                                        new Date().toISOString().substr(0, 10)
                                      "
                                                            min="1950-01-01"
                                                            @change="modalFn = false"
                                                    ></v-date-picker>
                                                </v-dialog>
                                            </v-col>
                                            <v-col cols="12" class="text-center">
                                                <v-btn @click="join()" large color="#F75028" class="font-blink font-weight-bold title white--text">¡Registrarme!</v-btn>
                                            </v-col>
                                            <v-col cols="12" class="py-0 my-0">
                                                <v-card
                                                        class="mx-auto"
                                                        style="background: rgb(0,0,0,.8)"
                                                        dark
                                                        max-width="600"
                                                >
                                                    <v-card-text class="headline font-weight-bold text-center my-0 py-0">
                                                        <v-row>
                                                            <v-col cols="12" class="clock-text mb-0 pb-0">
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock">{{REMAINING_DAYS.toString().padStart(2,'0')}}</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock-separator">:</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock">{{REMAINING_HOURS.toString().padStart(2,'0')}}</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock-separator">:</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock">{{REMAINING_MINUTES.toString().padStart(2,'0')}}</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock-separator">:</span>
                                                                <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.4em':'font-size: 2em'" class="clock">{{REMAINING_SECONDS.toString().padStart(2,'0')}}</span>
                                                            </v-col>
                                                            <v-col cols="12" class="clock clock-text mt-0 pt-0" :style="$vuetify.breakpoint.smAndDown?'font-size: .6em':'font-size: .8em'">
                                                                DIAS - HORAS - MINUTOS - SEGUNDOS
                                                            </v-col>
                                                        </v-row>
                                                    </v-card-text>
                                                </v-card>
                                            </v-col>
                                        </v-row>
                                    </v-form>
                                </v-card-text>
                            </v-card>
                        </v-col>
                    </v-row>
                    <v-row v-if="end && !showForm">
                        <v-col cols="12">
                            <div class="text-center font-blink white--text font-weight-bold mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 3em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                TODOS LOS MISTERIOS ESTÁN A PUNTO DE SER DESCUBIERTOS.</div>
                        </v-col>
                        <v-col cols="12">
                            <div class="text-center font-blink white--text mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 1.8em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 1.2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                Quédate pendiente porque pronto te daremos noticias increíbles</div>
                            <div class="text-center font-blink white--text mb-4" :style="$vuetify.breakpoint.mdAndUp?'font-size: 1.8em; line-height: 1em; text-shadow: 2px 2px 4px #000000':'font-size: 1.2em; line-height: 1em; text-shadow: 2px 2px 4px #000000'">
                                ¡No te despegues!</div>
                        </v-col>
                        <v-col cols="12">
                            <v-card
                                    class="mx-auto"
                                    style="background: rgb(0,0,0,.5)"
                                    dark
                            >
                                <v-card-text class="headline font-weight-bold text-center mb-0">
                                    <v-row>
                                        <v-col cols="12" class="clock-text mb-0 pb-0">
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_DAYS.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_HOURS.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_MINUTES.toString().padStart(2,'0')}}</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock-separator">:</span>
                                            <span :style="$vuetify.breakpoint.smAndDown?'font-size: 1.6em':''" class="clock">{{REMAINING_SECONDS.toString().padStart(2,'0')}}</span>
                                        </v-col>
                                        <v-col cols="12" class="clock clock-text mt-0 pt-0" :style="$vuetify.breakpoint.smAndDown?'font-size: .6em':'font-size: .8em'">
                                            DIAS - HORAS - MINUTOS - SEGUNDOS
                                        </v-col>
                                    </v-row>
                                </v-card-text>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-card-text>
            </v-card>
        </v-row>
        <v-dialog
                v-model="dialog"
                persistent
                max-width="600"
        >
            <v-card>
                <v-card-title class="headline">
                    Política de Cookies
                </v-card-title>
                <v-card-text>
                    En esta web se utilizan cookies de terceros y propias para conseguir
                    que tengas una mejor experiencia de navegación, si permanece aquí acepta su uso.
                    Puede leer más sobre el uso de cookies en nuestra <a href="/privacidad">política de privacidad</a>.
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                            color="green darken-1"
                            text
                            @click="aceptar()"
                    >
                        Aceptar
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-container>
</template>

<script>
    import { RULES } from "../mixins/rules";
    import axios from "axios";
    import moment from 'moment';
export default {
  name: "Home",
  mixins: [RULES],
  data: () => ({
      loading: false,
      sending: false,
      var: false,
      modalFn: false,
      dialog: false,
      showForm: false,
      end: false,
      days: 11,
      hours: 24,
      minutes: 59,
      seconds: 59,
      DATE_TARGET: moment().add(7,'days'),
      MILLISECONDS_OF_A_SECOND: 1000,
      MILLISECONDS_OF_A_MINUTE: 0,
      MILLISECONDS_OF_A_HOUR: 0,
      MILLISECONDS_OF_A_DAY: 0,
      REMAINING_DAYS: 0,
      REMAINING_HOURS: 0,
      REMAINING_MINUTES: 0,
      REMAINING_SECONDS: 0,
      formJoin: {
          nombre: "",
          apellido: "",
          correo: "",
          fechaNacimiento: ""
      },
  }),
  created() {},
  mounted() {
      this.MILLISECONDS_OF_A_MINUTE = this.MILLISECONDS_OF_A_SECOND * 60;
      this.MILLISECONDS_OF_A_HOUR = this.MILLISECONDS_OF_A_MINUTE * 60;
      this.MILLISECONDS_OF_A_DAY = this.MILLISECONDS_OF_A_HOUR * 24;

      this.updateCountdown();
      setInterval(this.updateCountdown, this.MILLISECONDS_OF_A_SECOND);
  },
  computed: {
      computedDateFormatted() {
          return this.formatDate(this.formJoin.fechaNacimiento);
      }
  },
  watch: {
      modalFn(val) {
          val && this.$nextTick(() => (this.$refs.picker.activePicker = "YEAR"));
      }
  },
  methods: {
      goSite(){
        location.href = "https://legocollectors-site.netlify.app"
      },
      formatDate(date) {
          if (!date) return null;
          const [year, month, day] = date.split("-");
          return `${day}/${month}/${year}`;
      },
      aceptar(){
          this.dialog = false;
      },
      updateCountdown() {
        // Calcs
        const NOW = new Date()
        const DURATION = this.DATE_TARGET - NOW;
        this.REMAINING_DAYS = Math.floor(DURATION / this.MILLISECONDS_OF_A_DAY);
        this.REMAINING_HOURS = Math.floor((DURATION % this.MILLISECONDS_OF_A_DAY) / this.MILLISECONDS_OF_A_HOUR);
        this.REMAINING_MINUTES = Math.floor((DURATION % this.MILLISECONDS_OF_A_HOUR) / this.MILLISECONDS_OF_A_MINUTE);
        this.REMAINING_SECONDS = Math.floor((DURATION % this.MILLISECONDS_OF_A_MINUTE) / this.MILLISECONDS_OF_A_SECOND);
    },
    join() {
      this.error = '';
      if (this.$refs.formJoin.validate()) {
          this.sending = true;
          axios
              .post("/functions/save.php", {
                  email: this.formJoin.correo,
                  name: this.formJoin.nombre,
                  lastname: this.formJoin.apellido,
                  birthday: this.formJoin.fechaNacimiento
              })
              .then(response => {
                  if (response.data.result) {
                      this.showForm = false;
                      this.end = true;
                  }else{
                      this.error = response.data.msg;
                  }
              })
              .catch(err => {
                  this.loading = false;
                  this.sending = false;
              })
              .finally(() => {
                  this.loading = false;
                  this.sending = false;
              });
      } else {
          console.log("errores en formulario");
      }
    },
  }
};
</script>
<style scoped>
    .v-text-field--outlined >>> fieldset {
        border-color: #E44420;
    }
</style>
