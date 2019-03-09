<template>
  <div id="app">
    <router-view></router-view>
    <div class="backPage" v-if="this.flag"></div>
  </div>
</template>

<script>
  import {mapState} from 'vuex'
  import Bus from '../src/common/bus.js'
  export default {
    name: 'vue-ele',
    computed: {
      ...mapState([
        'flag'
      ])
    },
    data(){
      return{
        color:[333,444,555,666,777,88,99,10,11,12,13,14,15,16,17,18,19,20,21,22],
        Strength:[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19],
        arr:[]
      }
    },
    created(){
      console.log(this.isSignal(-41,1,-100))

    },
    methods:{
      isSignal(num,i,z){

        let c = '';
        console.log(z)
        if(num<z){
          console.log(this.Strength[i])
          console.log(z)
          c = this.Strength[i];
        }else{
          i++;
          let j = 4;
          if(z>-41){
            j=5;
          }else if(z>-30){
            j=10;
          }

          this.isSignal(num,i,(z+j));
        }




      }
    },
    mounted(){
      this.$nextTick((res) => {
        let body = document.getElementsByTagName('body')[0]
        Bus.$on('click', (e) => {
          if(e){
            body.className = 'add_bg'
          }else{
            body.className = ''
          }
        })
      })
    },
  }
</script>

<style>
  .add_bg{
    overflow: hidden!important;
  }
  .backPage{
    position: fixed;
    z-index: 1;
    background: rgba(0,0,0,.4);
    left: 0;
    bottom: 0;
    top: 0;
    right: 0;
    overflow-x: hidden;
  }
</style>
