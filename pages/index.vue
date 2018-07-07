<template>
<div>
  <v-container fluid class="fullContainer px-0">
    <v-layout column text-xs-center>
      <v-flex xs12 class="mb-3">
        <h1>What would you like?</h1>
        <div class="cup mt-3">
          <svg version="1.1" x="0px" y="0px" width="100%" height="150px" viewBox="0 100 501 301" xml:space="preserve">
            <linearGradient id="gradient" x2="0%" y2="100%">
              <!-- c or o -->
              <stop v-if="coffeeTea !== '' && dai === '' && oc === ''" offset="20%" stop-color="#F3B146"/>
              <stop v-if="coffeeTea !== '' && dai === '' && oc === 'c'" offset="20%" stop-color="#fffde5"/>

              <stop v-if="coffeeTea !== '' && oc === '' && dai === 'siu dai'" offset="10%" stop-color="#F3B146"/>
              <stop v-if="coffeeTea !== '' && oc === '' && dai === 'ga dai'" offset="30%" stop-color="#F3B146"/>

              <stop v-if="coffeeTea !== '' && oc === 'c' && dai === 'siu dai'" offset="10%" stop-color="#fffde5"/>
              <stop v-if="coffeeTea !== '' && oc === 'c' && dai === 'ga dai'" offset="30%" stop-color="#fffde5"/>
              
              <!-- po or gao -->
              <stop v-if="coffeeTea === 'kopi' && poGao === 'gao'" stop-color="#45392D"/>
              <stop v-if="coffeeTea === 'kopi' && poGao === 'po'" stop-color="#CB9C7A"/>
              <stop v-if="coffeeTea === 'teh' && poGao === 'gao'" stop-color="#a56415"/>
              <stop v-if="coffeeTea === 'teh' && poGao === 'po'" stop-color="#d19955"/>

              <stop v-if="coffeeTea === 'yin yang' && poGao === 'po'" stop-color="#d19955"/>
              <stop v-if="coffeeTea === 'yin yang' && poGao === 'po'" offset="50%" stop-color="#CB9C7A"/>

              <stop v-if="coffeeTea === 'yin yang' && poGao === 'gao'" stop-color="#a56415"/>
              <stop v-if="coffeeTea === 'yin yang' && poGao === 'gao'" offset="50%" stop-color="#45392D"/>

              <!-- basic -->

              <stop v-if="coffeeTea === 'kopi' && poGao === ''" stop-color="#865f43"/>
              <stop v-if="coffeeTea === 'teh' && poGao === ''" stop-color="#C18232"/>
              <stop v-if="coffeeTea === 'yin yang' && poGao === ''" stop-color="#C18232"/>
              <stop v-if="coffeeTea === 'yin yang' && poGao === ''" offset="50%" stop-color="#865f43"/>

            </linearGradient>
          <style type="text/css">
            .bg{fill:#424242;}
            .steam{stroke:#FFF; fill: none; stroke-width: 2px;}
            .cup{fill:#FFF;stroke:#333;stroke-width:2;stroke-miterlimit:10;}
            .liquid{fill:url(#gradient) ;stroke:#351F02;stroke-miterlimit:10;}
            .sleeve{fill:#821200;}
            .lid{fill:#fff;stroke:#333;stroke-width:2;stroke-miterlimit:10;}
            .sugar{stroke: #333}
          </style>
          <defs>
            <mask id="liquidMasked">
              <path fill="#FFF" d="M294.3,377.1c-32.8,9.4-68.2,9.3-101-0.2c-7.1-60.7-14.1-119.7-21.5-175.6c48.3,0,96.5,0,144.8,0 C309,257.2,301.7,316.3,294.3,377.1z"/>
            </mask>
          </defs>
          <!-- <rect x="0.5" y="0.5" class="bg" width="500" height="500"/> -->
          <path class="cup" d="M301.4,382.2c-37.4,10.4-77.9,10.3-115.2-0.3c-8.1-66.7-16.1-131.6-24.5-193c55.1,0,110.1,0,165.2,0
          C318.1,250.3,309.8,315.3,301.4,382.2z"/>
          <g id="coffeeMasked" mask="url(#liquidMasked)">
          <path class="liquid" d="M293.8,376.6c-32.8,9.4-68.2,9.3-101-0.2c-7.1-60.7-14.1-119.7-21.5-175.6c0,0,12-7.1,31.3-0.4
          c29.8,10.3,32.7-0.2,48.7-0.2c27.4,0,29.2,8.8,44.7,1.3c14.7-7.1,20.2-0.7,20.2-0.7C308.5,256.7,301.2,315.8,293.8,376.6z"/>
          </g>
          <g v-if="peng === ''" class="steam">
          <path d="M308.5,169c0,0-16.5-17-13-32.5s22-5.5,13.5,6c-7.9,10.6-23.8-6.9-12-21.8c11.5-14.5,10.7-22,10-24.8
          c-5-18.4-18.6-5.8-12.6-1.1c9.4,7.1,15.2-16.5,13.2-24.5"/>
          </g>
            <path class="lid" d="M337.2,187v13.8c0,0-15.8,3.7-92,3.7s-92-3.7-92-3.7V187c0-1.8,1.4-3.2,3.2-3.2h5.8v-11.5
            c0-3.6,2.9-6.5,6.5-6.5h131.8l3.4,2.2c1.1,0.7,2.5,0.7,3.7,0l3.7-2.2h10.9c3.3,0,6.1,2.7,6.1,6.1v11.9h5.8
            C335.8,183.8,337.2,185.2,337.2,187z"/>
          </svg>
        </div>
        <v-avatar size="20px" tile>
          <img v-if="kosong !== 'kosong'" src="@/static/img/sugar.png" alt="Sugar">
        </v-avatar>
        <v-avatar size="20px" tile>
          <img v-if="dai !== 'siu dai' && kosong !== 'kosong'" src="@/static/img/sugar.png" alt="Sugar">
        </v-avatar>
        <v-avatar size="20px" tile>
          <img v-if="dai === 'ga dai'" src="@/static/img/sugar.png" alt="Sugar">
        </v-avatar>
      </v-flex>

      <v-flex>
        <v-btn round depressed :class="{ 'active': coffeeTea === 'kopi'}" @click.prevent="chooseCoffeeTea('kopi')">{{ english ? 'Coffee' : 'Kopi' }}</v-btn>
        <v-btn round depressed :class="{ 'active': coffeeTea === 'teh'}" @click.prevent="chooseCoffeeTea('teh')">{{ english ? 'Tea' : 'Teh' }}</v-btn>
        <v-btn round depressed :class="{ 'active': coffeeTea === 'yin yang'}" @click.prevent="chooseCoffeeTea('yin yang')">{{ english ? 'Coffee + Tea' : 'Yin Yang' }}</v-btn>
      </v-flex>

      <v-flex xs12>
        <v-btn round depressed :class="{ 'active': oc === 'o'}" @click.prevent="chooseOC('o')">{{ english ? 'No milk' : 'o' }}</v-btn>
        <v-btn round depressed :class="{ 'active': oc === 'c'}" @click.prevent="chooseOC('c')">{{ english ? 'Evaporated milk' : 'c' }}</v-btn>
      </v-flex>
      
      <v-flex xs12 v-if="kosong === ''">
        <v-btn round depressed :class="{ 'active': dai === 'siu dai'}" @click.prevent="chooseDai('siu dai')">{{ english ? 'Less sweet' : 'siu dai' }}</v-btn>
        <v-btn round depressed :class="{ 'active': dai === 'ga dai'}" @click.prevent="chooseDai('ga dai')">{{ english ? 'More sweet' : 'ga dai' }}</v-btn>
      </v-flex>

      <v-flex xs12 v-if="dai === ''">
        <v-btn round depressed :class="{ 'active': kosong === 'kosong'}" @click.prevent="chooseKosong('kosong')">{{ english ? 'No sugar' : 'kosong' }}</v-btn>
      </v-flex>

      <v-flex xs12>
        <v-btn round depressed :class="{ 'active': peng === 'peng'}" @click.prevent="choosePeng('peng')">{{ english ? 'Iced' : 'peng' }}</v-btn>
      </v-flex>

      <v-flex xs12>
        <v-btn round depressed :class="{ 'active': poGao === 'po'}" @click.prevent="choosePoGao('po')">{{ english ? 'Less thick' : 'po' }}</v-btn>
        <v-btn round depressed :class="{ 'active': poGao === 'gao'}" @click.prevent="choosePoGao('gao')">{{ english ? 'Thicker' : 'gao' }}</v-btn>
      </v-flex>

      <v-flex xs12>
        <v-btn small flat @click.prevent="english = !english" :class="{ 'active': english }">
          <div class="caption"><em>You first time in Singapore ah?</em></div>
        </v-btn>
      </v-flex>

    </v-layout>
  </v-container>

<div class="bottomBtn">
  <v-btn block large class="orderBtn ma-0" dark @click="openDialog()">Order</v-btn>
</div>

  
  <v-dialog v-model="nameDialog" fullscreen hide-overlay transition="dialog-bottom-transition">
    <v-card class="dialogCard">
      <v-btn icon dark @click.native="nameDialog = false">
        <v-icon>close</v-icon>
      </v-btn>
        <v-layout text-xs-center column class="px-3 mt-5">
            <h1>Your name is...</h1>
          <v-flex xs12>
            <v-text-field
              class="nameText"
              ref="nameText"
              autofocus
              rows=2
              v-model="name"
            ></v-text-field>
          </v-flex>
          
          <v-flex xs12>
          </v-flex>
        </v-layout>
            <h3 class="orderSummary">{{ order }}</h3>

        <div class="bottomBtn">
          <v-btn block large class="orderBtn ma-0" dark @click.prevent="sendOrder()">OK</v-btn>
        </div>

    </v-card>
  </v-dialog>
</div>
</template>

<script>
import axios from 'axios'

const airtableConfigs = {
  headers: { 'Authorization': 'Bearer ' + process.env.AIRTABLE_API_KEY }
}

export default {
  data () {
    return {
      nameDialog: false,
      coffeeTea: 'kopi',
      oc: '',
      dai: '',
      kosong: '',
      peng: '',
      poGao: '',
      english: false,
      name: ''
    }
  },
  computed: {
    order () {
      return `${this.coffeeTea} ${this.oc} ${this.dai} ${this.kosong} ${this.peng} ${this.poGao}`
    }
  },
  methods: {
    sendOrder () {
      const base = 'appArsQGp5U0Ex2BW'
      try {
        axios.post(
          `https://api.airtable.com/v0/${base}/Table%201?`,
          {
            'fields': {
              'Name': this.name,
              'Order': this.order
            }
          },
          airtableConfigs)
        this.$router.push('/thankyou')
      } catch (err) {
        console.log(err)
      }
    },
    openDialog () {
      this.nameDialog = true
      this.$refs.nameText.focus()
    },
    chooseCoffeeTea (val) {
      this.coffeeTea = val
    },
    chooseOC (val) {
      if (this.oc === val) {
        this.oc = ''
      } else {
        this.oc = val
      }
    },
    chooseDai (val) {
      if (this.dai === val) {
        this.dai = ''
      } else {
        this.dai = val
      }
    },
    chooseKosong (val) {
      if (this.kosong === val) {
        this.kosong = ''
      } else {
        this.kosong = val
      }
    },
    choosePeng (val) {
      if (this.peng === val) {
        this.peng = ''
      } else {
        this.peng = val
      }
    },
    choosePoGao (val) {
      if (this.poGao === val) {
        this.poGao = ''
      } else {
        this.poGao = val
      }
    }
  },
  // workaround for dialog form not autofocusing
  watch: {
    nameDialog (val) {
      if (!val) return
      requestAnimationFrame(() => {
        this.$refs.nameText.focus()
      })
    }
  }
}
</script>

<style scoped>
.active {
   background-color: #A8C4FF !important;
}

.nameText {
  line-height: 1.5em !important;
  font-size: 33px !important;
}

.orderBtn {
  background-color: #40392A !important;
}

.dialogCard {
  background-color: #A8C4FF !important;
}

.orderSummary {
  position: absolute;
  bottom: 80px;
  text-align: center;
  text-align: center;
  width: 100%;
}

.orderSummary {
  text-transform: capitalize;
}

/* cup */
.container{
   transform: translate(-50%, -50%);
   position: absolute;
   top: 50%;
   left: 50%;
}

/* ANIMATE LIQUID FILL */
.liquid {
   transform: translateX(100%);
   transform: translateY(100%);
   opacity: 0.8;
   animation: fill 3.2s;
   animation-fill-mode: forwards;
}

@keyframes fill {
   0% {
      opacity: 0.5;
      transform: translateY(100%);
   }
   100% {
      transform: translateY(0);
      opacity: 1;
      stroke: none;
   }
}

/* ANIMATE STEAM */
.steam {
   stroke: #F7F7F7;
   stroke-width: 1.5px;
   stroke-dasharray: 200;
   stroke-dashoffset: 200;
   opacity: 1;
   animation: steamAnimate 2.5s;
   animation-delay: 1s;
   animation-fill-mode: forwards;
}

@keyframes steamAnimate{
	0%{
		stroke-dashoffset: 200;
	}
	  
	100%{
		stroke-dashoffset: 0;
	}
}
</style>

