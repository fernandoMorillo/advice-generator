<template>
  <div class="container">
    <card-consejo></card-consejo>
  </div>
</template>

<script>
import CardConsejo from "@/components/Card-consejo";
export default {
  components: {
    CardConsejo,
  },
}
</script>

<style lang="scss">
@import "assets/css/variables";
@import "assets/css/fonts";


body {
  background-color: $Dark-Blue;
  font-family: $font-text;
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;

    h1 {
      color: $Neon-Green;
    }
  }


}



</style>
