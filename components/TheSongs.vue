<template>
  <div class="song">
    <div class="song__info">
      <div class="song_playOrPause">
        <button class="btn" @click="playOne">
          <img
            ref="imgOne"
            src="https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg"
            alt=""
          />
        </button>
      </div>
      <div class="song__autor">Dj Fletch&Eminem</div>
      <div class="song__name">Illest Motherfucker Alive</div>
      <div class="audio">
        <audio
          ref="audioOne"
          :src="newPathSongOne"
          @timeupdate="progressOne"
        ></audio>
      </div>
    </div>
    <div
      class="song__prgoress--container"
      ref="progressContOne"
      @click="setProgressOne"
    >
      <div class="song__progress" ref="progressProcOne"></div>
    </div>
  </div>

  <div class="song">
    <div class="song__info">
      <div class="song_playOrPause">
        <button class="btn" @click="playTwo">
          <img
            ref="imgTwo"
            src="https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg"
            alt=""
          />
        </button>
      </div>
      <div class="song__autor">Eminem</div>
      <div class="song__name">Not afraid</div>
      <div class="audio">
        <audio
          ref="audioTwo"
          :src="newPathSongTwo"
          @timeupdate="progressTwo"
        ></audio>
      </div>
    </div>
    <div
      class="song__prgoress--container"
      ref="progressContTwo"
      @click="setProgressTwo"
    >
      <div class="song__progress" ref="progressProcTwo"></div>
    </div>
  </div>

  <div class="song">
    <div class="song__info">
      <div class="song_playOrPause">
        <button class="btn" @click="playThree">
          <img
            ref="imgThree"
            src="https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg"
            alt=""
          />
        </button>
      </div>
      <div class="song__autor">Eminem</div>
      <div class="song__name">Soap</div>
      <div class="audio">
        <audio
          ref="audioThree"
          :src="newPathSongThree"
          @timeupdate="progressThree"
        ></audio>
      </div>
    </div>
    <div
      class="song__prgoress--container"
      ref="progressContThree"
      @click="setProgressThree"
    >
      <div class="song__progress" ref="progressProcThree"></div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api';
import pathSongOne from '../audio/Dj Fletch & Eminem - Illest Motherfucker Alive.mp3';
import pathSongTwo from '../audio/Eminem - Not afraid.mp3';
import pathSongThree from '../audio/Eminem - Soap.mp3';

export default defineComponent({
  setup() {
    const newPathSongOne = pathSongOne;
    const audioOne = ref(null);
    const imgOne = ref(null);
    const progressProcOne = ref(null);
    const progressContOne = ref(null);

    const newPathSongTwo = pathSongTwo;
    const audioTwo = ref(null);
    const imgTwo = ref(null);
    const progressProcTwo = ref(null);
    const progressContTwo = ref(null);

    const newPathSongThree = pathSongThree;
    const audioThree = ref(null);
    const imgThree = ref(null);
    const progressProcThree = ref(null);
    const progressContThree = ref(null);

    let counterOne = 0;
    let counterTwo = 2;
    let counterThree = 3;

    const playOne = () => {
      if (audioTwo.value.play() || audioThree.value.play()) {
        imgTwo.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioTwo.value.pause();

        imgThree.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioThree.value.pause();

        imgOne.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioOne.value.play();
      }

      if (counterOne === 0) {
        counterTwo = 2;
        counterThree = 3;

        imgOne.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioOne.value.play();

        counterOne++;
      } else {
        imgOne.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioOne.value.pause();

        counterOne--;
      }
    };

    const progressOne = (e) => {
      const { duration, currentTime } = e.srcElement;
      const progressProcent = (currentTime / duration) * 100;

      progressProcOne.value.style.width = `${progressProcent}%`;
    };

    const setProgressOne = (e) => {
      const width = progressContOne.value.clientWidth;
      const clickWidthX = e.offsetX;
      const duration = audioOne.value.duration;

      audioOne.value.currentTime = (clickWidthX / width) * duration;
    };

    const playTwo = () => {
      if (audioOne.value.play() || audioThree.value.play()) {
        imgOne.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioOne.value.pause();

        imgThree.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioThree.value.pause();

        imgTwo.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioTwo.value.play();
      }

      if (counterTwo === 2) {
        counterOne = 0;
        counterThree = 3;

        imgTwo.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioTwo.value.play();

        counterTwo++;
      } else {
        imgTwo.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioTwo.value.pause();

        counterTwo--;
      }
    };

    const progressTwo = (e) => {
      const { duration, currentTime } = e.srcElement;
      const progressProcent = (currentTime / duration) * 100;

      progressProcTwo.value.style.width = `${progressProcent}%`;
    };

    const setProgressTwo = (e) => {
      const width = progressContTwo.value.clientWidth;
      const clickWidthX = e.offsetX;
      const duration = audioTwo.value.duration;

      audioTwo.value.currentTime = (clickWidthX / width) * duration;
    };

    const playThree = () => {
      if (audioOne.value.play() || audioTwo.value.play()) {
        imgOne.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioOne.value.pause();

        imgTwo.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioTwo.value.pause();

        imgThree.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioThree.value.play();
      }

      if (counterThree === 3) {
        counterOne = 0;
        counterTwo = 2;

        imgThree.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/pause.svg';
        audioThree.value.play();

        counterThree++;
      } else {
        imgThree.value.src =
          'https://music.yandex.ru/node_modules/@yandex-music-int/music-ui/blocks/d-icon/white/play.svg';
        audioThree.value.pause();

        counterThree--;
      }
    };

    const progressThree = (e) => {
      const { duration, currentTime } = e.srcElement;
      const progressProcent = (currentTime / duration) * 100;

      progressProcThree.value.style.width = `${progressProcent}%`;
    };

    const setProgressThree = (e) => {
      const width = progressContThree.value.clientWidth;
      const clickWidthX = e.offsetX;
      const duration = audioThree.value.duration;

      audioThree.value.currentTime = (clickWidthX / width) * duration;
    };

    return {
      newPathSongOne,
      audioOne,
      playOne,
      imgOne,
      progressOne,
      progressProcOne,
      progressContOne,
      setProgressOne,
      newPathSongTwo,
      audioTwo,
      playTwo,
      imgTwo,
      progressTwo,
      progressProcTwo,
      progressContTwo,
      setProgressTwo,
      newPathSongThree,
      audioThree,
      playThree,
      imgThree,
      progressThree,
      progressProcThree,
      progressContThree,
      setProgressThree,
    };
  },
});
</script>

<style scoped>
.btn img {
  width: 48px;
}

.btn img:hover {
  box-shadow: 0 0 4px #9fa6a8;
}

.song {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
}

.song__info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 50%;
  font-size: 27px;
}

.song__name {
  color: #777;
}

.song__prgoress--container {
  background: #e4e9ed;
  border-radius: 5px;
  width: 50%;
  height: 10px;
  display: inline-flex;
  align-items: center;
  margin: 0 auto;
  cursor: pointer;
}

.song__progress {
  background: #2b3c5b;
  border-radius: 5px;
  height: 6px;
  cursor: pointer;
}

@media (max-width: 1585px) {
  .btn img[data-v-0b077d3e] {
    width: 35px;
  }
  .song__info {
    font-size: 17px;
  }
}

@media (max-width: 1140px) {
  .song_playOrPause .btn img {
    width: 20px;
  }
  .song__info {
    font-size: 10px;
  }

  .song__prgoress--container {
    height: 6px;
  }

  .song__progress {
    height: 4px;
  }
}

@media (max-width: 700px) {
  .song_playOrPause .btn img {
    width: 14px;
  }
  .song__info {
    font-size: 10px;
    width: 62%;
  }

  .song__prgoress--container {
    width: 38%;
    height: 4px;
  }

  .song__progress {
    height: 2px;
  }
}

@media (max-width: 550px) {
  .song_playOrPause .btn img {
    width: 10px;
  }
  .song__info {
    font-size: 8px;
    width: 65%;
  }

  .song__prgoress--container {
    width: 35%;
    height: 4px;
  }

  .song__progress {
    height: 2px;
  }
}
</style>
