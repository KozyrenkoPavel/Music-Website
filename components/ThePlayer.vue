<template>
  <div class="player">
    <header class="header">
      <h1>Музыка</h1>
    </header>

    <div class="main">
      <h2 class="main__header">Плейлист</h2>

      <TheSongs />
    </div>
  </div>
</template>

<style scoped>
.player {
  width: 80%;
  margin: 0 auto;
  height: 100%;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  font-size: 33px;
}

.main {
  text-align: center;
}

.main__header {
  padding: 15px;
  font-size: 24px;
  color: #777;
}

@media (max-width: 1140px) {
  .player .header {
    font-size: 20px;
  }

  .main__header {
    font-size: 14px;
  }
}

@media (max-width: 700px) {
  .player .header {
    font-size: 15px;
  }

  .main__header {
    font-size: 12px;
  }
}
</style>
