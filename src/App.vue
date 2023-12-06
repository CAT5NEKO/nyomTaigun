<template>
  <div>
    <div
        v-for="nyomuka in nyomukas"
        :key="nyomuka.id"
        class="nyomuka"
        :style="{ top: nyomuka.top + 'px', left: nyomuka.left + 'px' }"
        @click="nyomukaClick(nyomuka)"
    >
      {{ nyomuka.symbol }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nyomukas: [],
    };
  },
  methods: {
    nyomukaClick(nyomuka) {
      const message = nyomuka.symbol === '🐧' ? 'おめでとうございます。あなたはにょむ化しました。' : 'ﾝﾆｬｺﾞｺﾞｺﾞｺﾞｺﾞｺﾞｺﾞ！';
      window.alert(message);
    },
  },
  mounted() {
    const screenWidth = window.innerWidth;
    const screenHeight = window.innerHeight;
    const getRandomPosition = () => Math.floor(Math.random() * (screenWidth - 50));


    for (let i = 0; i < 50; i++) {
      this.nyomukas.push({
        id: i,
        symbol: '🐧',
        top: getRandomPosition(),
        left: getRandomPosition(),
      });
    }

    this.nyomukas.push({
      id: 285,
      symbol: '🐈',
      top: getRandomPosition(),
      left: getRandomPosition(),
    });

    setInterval(() => {
      this.nyomukas.forEach((nyomuka) => {
        nyomuka.top = getRandomPosition();
        nyomuka.left = getRandomPosition();
      });
    }, 800);
  },
};
</script>

<style scoped>

.nyomuka {
  position: absolute;
  font-size: 36px;
  cursor: pointer;
}
</style>
