<script>
export default {
  components: {},
  data() {
    return {
      ans: "終極密碼",
      temp: null,
      minNum: 1,
      maxNum: 100,
      pwd: null
    }
  },
  created() {
    this.pwd = Math.floor(Math.random() * (this.maxNum - this.minNum + 1) + this.minNum);
    console.log(this.pwd);
  },
  methods: {
    checkAnswer() {
      if (this.temp < this.minNum || this.temp > this.maxNum) {
        alert("請輸入正確的數字")
        return;
      }
      if (this.temp < this.pwd) {
        this.minNum = this.temp;
        this.temp = null;
      }
      if (this.temp > this.pwd) {
        this.maxNum = this.temp;
        this.temp = null;
      }
      if (this.temp == this.pwd) {
        this.ans = "恭喜猜對了"
      }
    }
  }
}

</script>

<template>
  <div class="card">
    <h1 class="title text-center">{{ ans }}</h1>
    <div class="numInfo">
      <p id="min" class="">{{ minNum }}</p>
      <p class="">-</p>
      <p id="max" class="">{{ maxNum }}</p>
    </div>

    <input type="number" id="input" v-model="temp" />

    <button type="button" id="btn" v-on:click="checkAnswer">
      回答
    </button>
  </div>
</template>

<style lang="scss" scoped>
.card {
  padding: 36px;
  box-shadow: 3px 3px 3px #555;
  transition: 0.3s;
  background-color: #fff;
  border-radius: 5px;

  .title {
    font-size: 24px;
    text-align: center;
  }

  .numInfo {
    display: flex;
    justify-content: center;
    align-items: center;

    p {
      font-size: 48px;
    }
  }

  #input {
    margin: 14px;
  }

  #btn {
    font-size: 16px;
  }
}

.card:hover {
  scale: 1.05;
}
</style>