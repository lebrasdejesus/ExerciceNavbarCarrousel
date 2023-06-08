<template>
  <div>
    <ssr-carousel>
      <div class="slide h-40 bg-orange-500">Slide 1</div>
      <div class="slide h-40 bg-green-500">Slide 2</div>
      <div class="slide h-40 bg-blue-500">Slide 3</div>
    </ssr-carousel>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      dataFromAPi: [],
      sliders: []
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
