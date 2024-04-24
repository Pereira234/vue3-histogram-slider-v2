<template>
  <div>
    original
    <HistogramSlider
      style="margin: 200px auto"
      type="double"
      :width="900"
      :bar-height="110"
      :data="data"
      :prettify="prettify"
      :clip="true"
      :drag-interval="true"
      :hideFromTo="true"
      @finish="finish"
      :force-edges="false"
      :colors="['#4facfe', '#00f2fe']"
      :grid-num="2"
    />

    fork test
    <HistogramSlider
      style="margin: 200px auto"
      ref="hist"
      type="double"
      :width="900"
      :bar-height="110"
      :data="data_test"
      :clip="true"
      :drag-interval="true"
      :hideFromTo="true"
      @finish="finish"
      :force-edges="false"
      :colors="['#4facfe', '#00f2fe']"
      v-slot="{ reset }"
      :from="4"
      :to="8"
      resettable
    >
      <button @click="reset">Ah</button>
    </HistogramSlider>
  </div>
</template>

<script>
import HistogramSlider from './lib/HistogramSlider'
export default {
  data() {
    return {
      data: require('../resources/data.json').map((d) => new Date(d).valueOf()),
      data_test: [1, 2, 3, 4, 5, 6, 10, 2, 3, 4, 6, 7, 8, 9, 1, 1, 1],
      prettify: function (ts) {
        return new Date(ts).toLocaleDateString('en', {
          year: 'numeric',
          month: 'short',
          day: 'numeric'
        })
      }
    }
  },

  methods: {
    finish(val) {}
  },

  components: {
    HistogramSlider
  }
}
</script>
