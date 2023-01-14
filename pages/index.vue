<template>
  <div class="bg-[#28293D] min-h-screen h-[100%]">
    <div class="container mx-auto">
      <div class="flex flex-col">
        <h1 class="text-[35px] mt-10 font-bold text-white">Champions</h1>
        <div class="mt-5 flex flex-row gap-5">
          <div class="flex mb-10">
            <div
              @click="
                filterChampions('');
                selectedFilter = '';
              "
              v-bind:class="filterRoles('')"
              class="w-12 h-12 flex justify-center rounded-l-sm items-center duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/allTypes.svg" class="w-[18px]" />
            </div>
            <div
              @click="
                filterChampions('TOP');
                selectedFilter = 'TOP';
              "
              v-bind:class="filterRoles('TOP')"
              class="w-12 h-12 flex justify-center items-center duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/Top.svg" class="w-[18px]" />
            </div>
            <div
              @click="
                filterChampions('JUNGLE');
                selectedFilter = 'JUNGLE';
              "
              v-bind:class="filterRoles('JUNGLE')"
              class="w-12 h-12 flex justify-center items-center duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/Jungle.svg" class="w-[18px]" />
            </div>
            <div
              @click="
                filterChampions('MIDDLE');
                selectedFilter = 'MIDDLE';
              "
              v-bind:class="filterRoles('MIDDLE')"
              class="w-12 h-12 flex justify-center items-center duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/Mid.svg" class="w-[18px]" />
            </div>
            <div
              @click="
                filterChampions('BOTTOM');
                selectedFilter = 'BOTTOM';
              "
              v-bind:class="filterRoles('BOTTOM')"
              class="w-12 h-12 flex justify-center items-center duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/Bottom.svg" class="w-[18px]" />
            </div>
            <div
              @click="
                filterChampions('UTILITY');
                selectedFilter = 'UTILITY';
              "
              v-bind:class="filterRoles('UTILITY')"
              class="w-12 h-12 flex justify-center items-center rounded-r-sm duration-300 bg-[#3E3E5A]/75 border border-[#3E3E5A] cursor-pointer"
            >
              <img src="/img/Support.svg" class="w-[18px]" />
            </div>
          </div>

          <div
            class="flex flex-col relative"
            @click="showModalDifficulty = !showModalDifficulty"
          >
            <!-- 
              Para que funcione como en la web de Kaikoo

              <input
              v-if="!selectedValue"
              v-model="selectedDifficulty"
              type="text"
              placeholder="Difficulty"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            />
            <input
              v-if="selectedValue"
              v-model="selectedValue"
              type="text"
              placeholder="Difficulty"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            /> -->

            <!-- Para que sea en tiempo real -->
            <input
              v-model="selectedValue"
              type="text"
              placeholder="Difficulty"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            />
            <img
              v-if="!selectedValue"
              class="top-5 cursor-pointer right-3 absolute w-[10px] h-[10px]"
              src="/img/Flecha.svg"
            />
            <img
              @click="clearSelectedValue()"
              v-if="selectedValue"
              class="w-[10px] h-[10px] top-5 cursor-pointer right-3 absolute"
              src="/img/Cerrar.svg"
            />
            <div v-if="showModalDifficulty">
              <div
                class="z-50 top-16 max-h-40 overflow-y-scroll absolute bg-[#454563] border border-[#3E3E5A] border-l-0"
              >
                <div
                  v-for="(difficulty, index) in difficultyArray"
                  v-if="
                    difficulty
                      .toLowerCase()
                      .includes(selectedValue.toLowerCase()) // En tiempo real
                    //.includes(selectedDifficulty.toLowerCase()) -> Para que funcione como en la web de Kaikoo
                  "
                  @click="selectedValue = difficulty"
                  class="hover:bg-[#2b2a3a] bg-[#454563] w-[175px] flex items-center cursor-pointer pl-5 text-white py-4"
                >
                  {{ difficulty }}
                </div>
              </div>
            </div>
          </div>
          <div
            class="flex flex-col relative"
            @click="showModalSearch = !showModalSearch"
          >
            <!-- 
              Para que funcione como en la web de Kaikoo

              <input
              v-if="!searchValue"
              v-model="searchValueChampions"
              type="text"
              placeholder="Buscar campeón"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            /> 
              <input
              v-if="searchValue"
              v-model="searchValue"
              type="text"
              placeholder="Buscar campeón"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            /> -->

            <!-- Para que sea en tiempo real -->
            <input
              v-model="searchValue"
              type="text"
              placeholder="Buscar campeón"
              class="h-12 text-white w-[192px] px-4 bg-[#454563] border border-[#3E3E5A] focus:outline-0 rounded-sm"
            />
            <img
              v-if="!searchValue"
              class="top-5 cursor-pointer right-3 absolute w-[10px] h-[10px]"
              src="/img/Flecha.svg"
            />
            <img
              @click="clearSearchValue()"
              v-if="searchValue"
              class="w-[10px] h-[10px] top-5 cursor-pointer right-3 absolute"
              src="/img/Cerrar.svg"
            />
            <div v-if="showModalSearch">
              <div
                class="z-50 top-16 max-h-40 overflow-y-scroll absolute bg-[#454563] border border-[#3E3E5A] border-l-0"
              >
                <div
                  v-for="(champion, index) in championsData"
                  v-if="
                    champion.name
                      .toLowerCase()
                      .includes(searchValue.toLowerCase()) //Para sea en tiempo real
                    //.includes(searchValueChampions.toLowerCase()) -> Para que funcione como en la web de Kaikoo
                  "
                  @click="searchValue = champion.name"
                  class="hover:bg-[#2b2a3a] bg-[#454563] w-[175px] flex items-center cursor-pointer pl-5 text-white py-4"
                >
                  {{ champion.name }}
                </div>
              </div>
            </div>
          </div>
          <div class="flex">
            <button
              @click="showFavorites = !showFavorites"
              class="flex justify-center items-center bg-[#3E3E5A]/75 border border-[#3E3E5A] rounded-sm w-12 h-12"
            >
              <img v-if="showFavorites" src="/img/StarSelected.svg" />
              <img v-else src="/img/Star.svg" />
            </button>
          </div>
        </div>
      </div>
    </div>
    <Champions
      :championsData="filteredChampions"
      :toggle-favorite="toggleFavorite"
    />
  </div>
</template>

<script>
export default {
  name: "IndexPage",

  data() {
    return {
      data: {},
      selectedFilter: "",
      showModal: false,
      showModalDifficulty: false,
      showModalSearch: false,
      searchValue: "",
      // searchValueChampions: "",
      selectedValue: "",
      // selectedDifficulty: "",
      filterLanes: "",
      showFavorites: false,
      difficultyArray: ["Easy", "Average", "Hard", "Severe"],
    };
  },

  async asyncData({ $axios }) {
    const championsData = await $axios.$get("/api/champions");
    const championsDataWithFavorite = championsData.map((champion) => {
      return { ...champion, favorite: false };
    });
    return { championsData: championsDataWithFavorite };
  },

  methods: {
    filterChampions(value) {
      this.filterLanes = value;
    },
    filterRoles(role) {
      return {
        selected: this.selectedFilter === role,
      };
    },
    toggleFavorite(champion) {
      champion.favorite = !champion.favorite;
    },
    clearSelectedValue() {
      this.selectedValue = "";
      // this.selectedDifficulty = "";
    },
    clearSearchValue() {
      this.searchValue = "";
      // this.searchValueChampions = "";
    },
  },

  computed: {
    filteredChampions() {
      if (this.searchValue.trim().length > 0) {
        return this.championsData.filter((champions) =>
          champions.name
            .toLowerCase()
            .includes(this.searchValue.trim().toLowerCase())
        );
      }

      return this.championsData.filter((champion) => {
        if (this.selectedValue.trim().length > 0) {
          if (
            !champion.difficulty
              .toLowerCase()
              .includes(this.selectedValue.trim().toLowerCase())
          ) {
            return false;
          }
        }

        if (this.filterLanes) {
          if (!champion.lanes.includes(this.filterLanes)) {
            return false;
          }
        }

        if (this.showFavorites) {
          if (!champion.favorite) {
            return false;
          }
        }

        return true;
      });

      return this.championsData;
    },
  },
};
</script>
