<template>
  <div>
    <div id="time-layer">
      <h1>{{ time }}</h1>
    </div>
    <Buttons v-on:toggle="timer"/>
  </div>
</template>

<script>
import Buttons from './Buttons.vue'
export default {
  name: 'Clock',
  data() {
    return {
      time : "00:00:00",
      cron : ""
    }
  },
  components:{
    Buttons
  },
  methods: {
    timer(param){
        if ( param.status == 0 )

        {
            this.time = "00:00:00";
        }

        else if( param.status == 1 )

        {
          this.cron = setInterval(() => {
              var [h,m,s] = this.time.split(":").map(v => parseInt(v));
              if (s < 59){
                s++;
              }else{
                s = 0;
                if (m < 59){
                  m++;
                }else{
                  m = 0;
                  h++;
                }
              }

              h = h < 10 ? `0${h}` : h;
              m = m < 10 ? `0${m}` : m;
              s = s < 10 ? `0${s}` : s;

              this.time = `${h}:${m}:${s}`;
            }, 1000);
        }

        else if (param.status == 2)

        {
          clearInterval(this.cron);
        }

      }
    }


  }
</script>


<style scoped>
  #time-layer{
    width: 100vw;
    height: 50vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #1b1b1e;
    color: white;
    font-size: 2.5rem;
    position: absolute;
    overflow: hidden;
  }
</style>
