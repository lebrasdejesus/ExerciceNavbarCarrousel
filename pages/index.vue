<template>
  <div class="flex-column">
    <!-- navbar menu et sous menu-->
    <div class="z-10 relative">
      <!-- menu blanc -->
      <div
        class="flex flex-row place-content-between max-h-20 h-20 z-10 font-bold bg-white"
      >
        <!-- partie logo + nom concession -->
        <div class="flex flex-row justify-start basis-2/6 items-center">
          <div class="max-w-fit md:ml-16 ml-2 text-center">
            <img
              src="@/assets/images/logo_suzuki_horizontal_color.c4d2cbf.svg"
              alt="Logo Suzuki"
              class="h-20 md:h-24"
            />
          </div>
          <div class="flex w-48 my-4 mx-4">
            <span class="text-lg uppercase">{{ dataFromAPi.nameSeller }}</span>
          </div>
        </div>
        <!-- partie menu -->
        <div class="flex flex-row justify-end flex-wrap mr-8 z-10">
          <div class="px-3 text-xs h-full">
            <div
              class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950"
            >
              <div>Véhicules neufs</div>
            </div>
          </div>
          <div class="px-3 text-xs h-full">
            <div
              class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950"
            >
              <div>Occasions</div>
            </div>
          </div>
          <!-- menu service apres vente -->
          <div
            class="px-3 text-xs h-full"
            @mouseover="sousMenu = 1"
            @mouseleave="sousMenu = 0"
          >
            <div
              class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950"
            >
              <div>Service après-vente</div>
            </div>
          </div>

          <div
            class="px-3 text-xs h-full"
            @mouseover="sousMenu = 2"
            @mouseleave="sousMenu = 0"
          >
            <div
              class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950"
            >
              <div>Offres et actualités</div>
            </div>
          </div>
          <div
            class="px-3 text-xs h-full"
            @mouseover="sousMenu = 3"
            @mouseleave="sousMenu = 0"
          >
            <div
              class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950"
            >
              <div>La concession</div>
            </div>
          </div>
        </div>
      </div>

      <!-- conteneur global sous menu service apres vente -->
      <div
        class="flex flex-row w-full bg-white absolute"
        v-bind:class="[sousMenu === 1 ? '' : 'hidden']"
        @mouseover="sousMenu = 1"
        @mouseleave="sousMenu = 0"
      >
        <!-- conteneur du 1er bloc de gauche -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Après-vente</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Atelier mécanique</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Carosserie et pare-brise</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Prendre rendez-vous en atelier</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Offre après-vente</span>
          </div>
        </div>
        <!-- conteneur du 2eme bloc milieu -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Garanties et assistance</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Garantie et assistance Suzuki</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs"
              >Contrat d'entretien et extension de garantie</span
            >
          </div>
        </div>
        <!-- conteneur du 2eme bloc milieu -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Accessoires</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Tous les accessoires</span>
          </div>
        </div>
      </div>

      <!-- conteneur global sous menu offre et actualité -->
      <div
        class="flex flex-row w-full bg-white absolute"
        v-bind:class="[sousMenu === 2 ? '' : 'hidden']"
        @mouseover="sousMenu = 2"
        @mouseleave="sousMenu = 0"
      >
        <!-- conteneur du 1er bloc de gauche -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Nos offres</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Atelier mécanique</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Carosserie et pare-brise</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Prendre rendez-vous en atelier</span>
          </div>
        </div>
        <!-- conteneur du 2eme bloc milieu -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Notre actualité</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Garantie et assistance Suzuki</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs"
              >Contrat d'entretien et extension de garantie</span
            >
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Offre après-vente</span>
          </div>
        </div>
      </div>

      <!-- conteneur global sous menu la concession -->
      <div
        class="flex flex-row w-full bg-white absolute"
        v-bind:class="[sousMenu === 3 ? '' : 'hidden']"
        @mouseover="sousMenu = 3"
        @mouseleave="sousMenu = 0"
      >
        <!-- conteneur du 1er bloc de gauche -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Contact & acces</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Atelier mécanique</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Carosserie et pare-brise</span>
          </div>
        </div>
        <!-- conteneur du 2eme bloc milieu -->
        <div class="flex flex-col py-12 md:pl-16 pl-2 font-bold">
          <div class="flex flex-row py-2">
            <span class="text-2xl">Qui sommes nous ?</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs">Garantie et assistance Suzuki</span>
          </div>
          <div class="flex flex-row py-2">
            <span class="text-xs"
              >Contrat d'entretien et extension de garantie</span
            >
          </div>
        </div>
      </div>
    </div>

    <!-- caroussel -->
    <div>
      <ssr-carousel loop class="z-0">
        <div
          class="slide object-cover bg-orange-500 relative"
          v-for="slide in sliders"
          :key="slide.id"
        >
          <div
            class="grid content-center p-8 bg-gradient-to-r from-neutral-500 absolute inset-0 w-2/5"
          >
            <!-- texte slider -->
            <div class="text-lg lg:text-3xl uppercase w-10/12 md:w-full">
              <span class="text-white font-bold"
                >Profitez des jours simplissimes chez Suzuki !</span
              >
            </div>
            <!-- boutons slider-->
            <div class="grid grid-cols-2 w-full max-h-16 md:gap-6 mt-6 sm:mt-4">
              <div class="w-full">
                <div
                  class="flex flex-row justify-center cursor-pointer transition duration-300 ease-in-out rounded-md w-full bg-white hover:bg-zinc-200 text-black"
                >
                  <span class="text-xs lg:text-base font-semibold py-4"
                    >Réserver un essai</span
                  >
                </div>
              </div>
              <div class="w-full">
                <div
                  class="flex flex-row justify-center cursor-pointer transition duration-300 ease-in-out rounded-md w-full bg-blue-800 hover:bg-blue-900 text-white"
                >
                  <span class="text-xs lg:text-base font-semibold py-4"
                    >Voir l'offre</span
                  >
                </div>
              </div>
            </div>
          </div>

          <div>
            <img
              :src="slide.images.filter((x) => x.tag === 'desktop')[0]['@id']"
            />
          </div>
        </div>
        <!-- <div class="slide h-96 bg-orange-500">{{ sliders.images }}</div> -->
        <!-- <div class="slide h-96 bg-orange-500 style="background: (v-for="image in slide.images" :src="image['@id']" :key="image['@id']" )"></div> -->
      </ssr-carousel>

      <!-- <span class="now">Current Page: {{ page + 1 }}</span>
    <button @click='page--'>Back</button>
    <button @click='page++'>Next</button> -->
    </div>
    <div class="text-slate-100">Bonjour...</div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",

  data() {
    return {
      dataFromAPi: [],
      sliders: [],
      sousMenu: 0,
      // slidersDesktop: []
      // page: 0
    };
  },

  async fetch() {
    const { data: fromAPi } = await this.$axios.get(
      "https://dps-api-site-ce.herokuapp.com/locations?slug=la-rochelle"
    );
    this.dataFromAPi = fromAPi["hydra:member"][0];
    const { data: sliderFrom } = await this.$axios.get(
      `https://dps-api-site-ce.herokuapp.com${this.dataFromAPi["@id"]}/sliders`
    );
    this.sliders = sliderFrom["hydra:member"];
  },
};
</script>

<style scoped>
.cache {
  display: none;
}
</style>