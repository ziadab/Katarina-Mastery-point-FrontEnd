<template>
  <div class="container">
    <div class="dataSection">
      <fade-transition :duration="900" :delay="700">
        <div class="text_stuff" v-show="mastery > 0">
          <p class="text1">Your Mastery Point</p>
          <p class="text2">Are</p>
          <p class="mastery">{{ mastery }}</p>
        </div>
      </fade-transition>
    </div>
    <fade-transition :duration="900" :delay="100">
      <div class="imageSection" v-show="mastery > 0">
        <img class="kata" src="https://d.top4top.io/p_1718jgvml1.png" />
      </div>
    </fade-transition>
  </div>
</template>

<script>
import { FadeTransition } from "vue2-transitions";
import axios from "axios";

export default {
  data() {
    return {
      mastery: 0
    };
  },
  async mounted() {
    const request = await axios.get(
      "https://katarina-mastery-counter.herokuapp.com/"
    );
    this.mastery = request.data.mastery;
  },
  components: {
    FadeTransition
  }
};
</script>

<style>
.container {
  display: flex;
  height: 100vh;
}
.dataSection {
  flex: 1 1 0px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.text_stuff {
  margin-left: 100px;
}

p {
  font-family: "NowMedium";
  font-size: 48px;
}

.text2 {
  font-family: "NowBold";
}

.mastery {
  letter-spacing: 0.154em;
  color: #855f9c;
}

.imageSection {
  flex: 1 1 0px;
}

.kata {
  position: absolute;
  right: 0px;
  bottom: 0px;
}
</style>
