<template>
  <div class="container mx-auto pb-20 flex gap-4 flex-wrap">
    <div v-for="(champion, index) in championsData" :key="index">
      <div
        class="SquareChampion relative duration-300 flex flex-col text-center justify-center items-center"
        @mouseover="hover = index"
        @mouseout="hover = null"
        v-bind:class="{ 'SquareChampionHover duration-300': hover === index }"
      >
        <div
          class="background-image-container"
          v-bind:class="{ 'opacity-20': hover === index }"
        >
          <div
            class="background-image"
            v-bind:style="{
              backgroundImage:
                hover === index
                  ? `url(https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${champion.nameId}_0.jpg)`
                  : '',
              transition: 'background 3s linear',
            }"
          ></div>
        </div>
        <div class="absolute top-3 left-3">
          <div class="flex flex-col gap-2">
            <img
              v-if="champion.lanes.includes('JUNGLE')"
              src="../static/img/Jungle.svg"
            />
            <img
              v-if="champion.lanes.includes('MIDDLE')"
              src="../static/img/Mid.svg"
            />
            <img
              v-if="champion.lanes.includes('TOP')"
              src="../static/img/Top.svg"
            />
            <img
              v-if="champion.lanes.includes('BOTTOM')"
              src="../static/img/Bottom.svg"
            />
            <img
              v-if="champion.lanes.includes('UTILITY')"
              src="../static/img/Support.svg"
            />
          </div>
        </div>
        <div class="absolute bg-[#3e3e5acc] top-2 right-0 py-1 px-2 text-white">
          <p class="text-sm">{{ champion.difficulty }}</p>
        </div>
        <div
          @click="toggleFavorite(champion)"
          class="absolute bg-[#3e3e5acc] top-12 right-0 py-1 px-2 text-white cursor-pointer"
        >
          <img v-if="champion.favorite" src="/img/StarSelected.svg" />
          <img v-else src="/img/Star.svg" />
        </div>
        <div class="w-16 h-16">
          <img
            :src="`https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${champion.nameId}_0.jpg`"
            class="border-[2.6px] border-[#60609B] duration-300 object-cover w-full h-full rounded-full"
            v-bind:class="{ 'border-opacity-65 duration-300': hover === index }"
          />
        </div>
        <p class="font-bold text-xl text-white mt-4">
          {{ champion.name }}
        </p>
        <p class="text-[#ACACBE] text-sm mb-4">
          {{ champion.description_en }}
        </p>
        <div class="flex text-sm text-[#ACACBE]">
          <div class="px-2 flex flex-col justify-center items-center">
            <p>Early</p>
            <div class="mt-1">
              <img
                v-if="champion.gamePowerSpike[0] === 'normal'"
                src="../static/img/YellowLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[0] === 'strong'"
                src="../static/img/GreenLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[0] === 'weak'"
                src="../static/img/RedLine.svg"
              />
            </div>
          </div>
          <div class="px-2 flex flex-col justify-center items-center">
            <p>Mid</p>
            <div class="mt-1">
              <img
                v-if="champion.gamePowerSpike[1] === 'normal'"
                src="../static/img/YellowLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[1] === 'strong'"
                src="../static/img/GreenLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[1] === 'weak'"
                src="../static/img/RedLine.svg"
              />
            </div>
          </div>
          <div class="px-2 flex flex-col justify-center items-center">
            <p>Late</p>
            <div class="mt-1">
              <img
                v-if="champion.gamePowerSpike[2] === 'normal'"
                src="../static/img/YellowLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[2] === 'strong'"
                src="../static/img/GreenLine.svg"
              />
              <img
                v-if="champion.gamePowerSpike[2] === 'weak'"
                src="../static/img/RedLine.svg"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    championsData: Array,
    toggleFavorite: Function,
  },

  data() {
    return {
      hover: null,
    };
  },
};
</script>
