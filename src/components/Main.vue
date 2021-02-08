<template>
  <section class="hero is-fullheight is-info is-bold">
      <div class="hero-body">
          <div class="container has-text-centered">
              <h1 class="title">Adrift in the Harbor</h1>
              <h2 class="subtitle">Simple Gacha Counter</h2>
              <div class="counter-container">
                  <div class="counter-container-item">
                      <p class="counter-theme">{{currentCount}} </p>
                    </div>
                    <div class="counter-container-img">
                        <figure class="image is-128x128">
                            <img class="is-rounded" :src="require(`../assets/Chibi_Ganyu.jpg`)" alt="chibi_ganyu">
                        </figure>
                    </div>
                </div>
                <div class="add-buttons-container">
                    <div class="add-buttons-container-plus">
                        <button @click.prevent="add" class="button is-success is-rounded">+</button>
                    </div>
                    <div class="add-buttons-container-plus10">
                        <button @click.prevent="plus10" class="button is-success is-rounded">+10</button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            currentCount: 0
        }
    },
    methods: {
        add: function() {
            return this.currentCount = this.currentCount + 1;
            },
            plus10: function() {
                return this.currentCount = this.currentCount + 10;
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


</style>