<template>
  <section class="hero is-fullheight is-info is-bold">
      <div class="hero-body">
          <div class="container has-text-centered">
              <p>{{ timestamp }}</p>
              <BannerLabel />
              <h2 class="subtitle">Simple Gacha Counter</h2>
              <div class="counter-container">
                  <div class="counter-container-item">
                      <p class="counter-theme">{{currentCount}}</p>
                    </div>
                    <div class="counter-container-img">
                        <figure class="image is-128x128">
                            <img class="is-rounded" :src="require(`../assets/Chibi_Ganyu.jpg`)" alt="chibi_ganyu">
                        </figure>
                    </div>
                </div>
                <div class="add-buttons-container">
                    <div class="add-buttons-container-plus">
                        <button @click.prevent="add" class="styled-button round">+</button>
                    </div>
                    <div class="add-buttons-container-plus10">
                        <button @click.prevent="plus10" class="styled-button round">+10</button>
                    </div>
                </div>
                <div id="reset-btn-container">
                    <button @click.prevent="reset"  class="styled-button round red">Reset</button>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import { toast } from 'bulma-toast'
import BannerLabel from './BannerLabel'

export default {
    data() {
        return {
            currentCount: 0,
            timestamp: ''
        }
    },
    components: {
        BannerLabel
    },
    mounted() {
        setInterval(this.getDateTime, 1000);
    },
    methods: {
        getDateTime: function(){
            const dateString = new Date().toDateString();
            const timeString = new Date().toLocaleTimeString();
            const dateTimeString = dateString + " " + timeString;
            this.timestamp = dateTimeString;
        },
        add: function() {
            toast({
                message: 'You pulled 1 time at ' + this.timestamp,
                type: 'is-success',
                position: "top-center",
                dismissible: true,
                pauseOnHover: true,
                closeOnClick: true
            });
            this.currentCount ++;
        },
        plus10: function() {
             toast({
                message: 'You pulled 10 times at ' + this.timestamp,
                type: 'is-success',
                position: "top-center",
                dismissible: true,
                pauseOnHover: true,
                closeOnClick: true
            });
            this.currentCount = this.currentCount + 10;
        },
        reset: function() {
            this.currentCount = 0;
        }
    }
}
</script>

<style scoped>
    .counter-container {
        display: flex;
        justify-content: center;
        margin: 2rem 0rem;
    }
    .counter-container-item, .img-container-item {
        margin: 0rem 2rem;
    }
    
    .counter-theme {
        font-size: 90px;
    }

    .add-buttons-container {
        display: flex;
        justify-content: center;
    }

    .add-buttons-container-plus, .add-buttons-container-plus10 {
        margin: 0rem 1rem;
    }

    .styled-button {
        background-color: #48c774;
        color: #fff;
        font-weight: bold;
        font-size: 1rem;
        cursor: pointer;
        justify-content: center;
        padding-bottom: 1rem;
        padding-top: 1rem;
        border: 1.5px solid #fff;
        box-shadow:4px 4px #555555;
    }

    .round {
        border-radius: 2rem;
        padding-left: 2rem;
        padding-right: 2rem;
    }

    .red {
        background-color: #f14668;
    }

    .styled-button:hover {
        background: orange;
        border: 1.5px solid #fff;
    }

    .styled-button:active {
        border: 1.5px solid #fff;
        transform: translateY(4px);
    }

    #reset-btn-container {
        margin: 1.5rem 0;
    }

    @media screen and (max-width: 600px) {

        .counter-container, .add-buttons-container {
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .counter-container-item, .img-container-item, .add-buttons-container-plus, .add-buttons-container-plus10 {
            margin: 0.5rem 0;
        }
    }

</style>