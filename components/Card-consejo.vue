<template>
  <div class="d-flex justify-content-center">
    <b-card class="text-center">
      <b-card-title>ADVICE #{{ idConsejo }}</b-card-title>
      <transition name="bounce-in">
        <b-card-text class="py-4">
          <p>
          {{
          consejo === '' ? 'Presiona el dado para obtener tu consejo' : '" ' + consejo + ' "'
          }}
        </p>
        </b-card-text>
      </transition>
      <b-img class="my-3 pb-4" src="../static/img-principales/pattern-divider-mobile.svg"></b-img>
      <div class="container-dado" @click="searchConsejo">
        <b-img src="../static/img-principales/icon-dice.svg"></b-img>
      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Card-consejo",
  data() {
    return {
      idConsejo: 0,
      consejo: '',
    }
  },
  methods: {
    searchConsejo() {
      this.$axios.get('advice').then((res) => {
        this.consejo = res.data.slip.advice;
        this.idConsejo = res.data.slip.id;
      }).catch((error) => {
        console.log(error)
      })
    }
  }
}
</script>

<style scoped lang="scss">
@import "assets/css/variables";
@import "assets/css/fonts";

.card {
  background-color: $Dark-Grayish-Blue;
  position: relative;
  border-radius: 10px;
  font-family: $font-text;
  width: 470px;

  .card-title {
    color: $Neon-Green;
    font-size: $font-sm;
    letter-spacing: 4px;
    font-weight: 100;
  }
  .card-text {
    color: $Light-Cyan;
    font-size: $font-md;
    animation: bounce-in .5s;
    margin-bottom: 0;

    @keyframes bounce-in {
      0% {
        transform: scale(0);
      }
      50% {
        transform: scale(1.5);
      }
      100% {
        transform: scale(1);
      }
    }
    p {
      margin-bottom: 0;
    }
  }

  .container-dado {
    position: absolute;
    left: 45%;
    background-color: $Neon-Green;
    padding: 12px;
    border-radius: 50%;
    transition: transform ease 1s;
    cursor: pointer;
    box-shadow: 0 0 8px -1px $Neon-Green;

    img {
      animation: dado infinite 3.1s;
    }

    @keyframes dado {
      from {
        transform: rotate(0deg);
      }
      to {
        transform: rotate(360deg);
      }
    }
  }

  .container-dado:hover {
    transform: scale(1.1);
    box-shadow:  0 0 26px -1px hsl(150deg 100% 66%);
  }

  .container-dado:active {
    box-shadow: 0 0 26px -1px hsl(150deg 100% 66%);
  }

}

@media screen and (max-device-width: 425px) {
  .card {
    width: 366px;

    .container-dado {
      left: 44%;
    }
  }
}


</style>
