<template>
  <div class="container">
    <div class="dataSection">
      <div class="text_stuff">
        <p class="text1">Your Mastery Point</p>
        <p class="text2">Are</p>
        <p class="mastery">{{ mastery }}</p>
      </div>
    </div>
    <div class="imageSection">
      <img class="kata" src="https://d.top4top.io/p_1718jgvml1.png" />
    </div>
  </div>
</template>

<script>
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
