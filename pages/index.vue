<template>
  <div class="flex-column">
    <div class="flex flex-row max-h-24 h-24 z-10 font-bold">
      <div class="flex flex-row basis-1/2 items-center">
        <div class="max-w-fit	ml-16 max-w-xs text-center">
          <img src="@/assets/images/logo_suzuki_horizontal_color.c4d2cbf.svg" alt="Logo Suzuki" class="h-24"></div>
        <div class="flex w-48 my-4 mx-4">
          <span class="text-lg uppercase">{{ dataFromAPi.nameSeller }}</span>
        </div>
      </div>

      <div class="flex flex-row justify-end items-center basis-1/2 flex-wrap z-10">
        <div class="px-3 text-sm h-full">
          <div class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950">
            <div>Véhicules neufs</div>
          </div>
        </div>
        <div class="px-3 text-sm h-full">
          <div class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950">
            <div>Occasions</div>
          </div>
        </div>
        <div class="px-3 text-sm h-full">
          <div class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950">
            <div>Service après-vente</div>
          </div>
        </div>
        <div class="px-3 text-sm h-full">
          <div class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950">
            <div>Offres et actualités</div>
          </div>
        </div>
        <div class="px-3 text-sm h-full">
          <div class="flex h-full items-center border-b-4 border-spacing-y-12 border-transparent hover:border-indigo-950">
            <div>La concession</div>
        </div>
      </div>

      </div>
    </div>


    <div>
    <ssr-carousel show-dots loop class="z-0">
      <div class="slide h-96 bg-orange-500 relative" v-for='slide in sliders' :key='slide.id' > 
        <div class=" h-96 bg-gradient-to-r from-blue-500 absolute"></div> 
        <div><img class="object-none" :src="slide.images.filter(x => x.tag === 'desktop')[0]['@id']"/></div>
        
      </div>
      <!-- <div class="slide h-96 bg-orange-500">{{ sliders.images }}</div> -->
      <!-- <div class="slide h-96 bg-orange-500 style="background: (v-for="image in slide.images" :src="image['@id']" :key="image['@id']" )"></div> -->
    </ssr-carousel>

    <!-- <span class="now">Current Page: {{ page + 1 }}</span>
    <button @click='page--'>Back</button>
    <button @click='page++'>Next</button> -->
  </div>

  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      dataFromAPi: [],
      sliders: [],
      slidersDesktop: []
      // page: 0
    }
  },

  async fetch() {
    const { data: fromAPi } = await this.$axios.get('https://dps-api-site-ce.herokuapp.com/locations?slug=la-rochelle')
    this.dataFromAPi = fromAPi['hydra:member'][0]
    const { data: sliderFrom } = await this.$axios.get(`https://dps-api-site-ce.herokuapp.com${this.dataFromAPi['@id']}/sliders`)
    this.sliders = sliderFrom['hydra:member']
  }
}
</script>
