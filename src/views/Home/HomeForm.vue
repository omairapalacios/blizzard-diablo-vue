<template>
  <div class="search-form my-5">
    <div class="row">
      <div class="col-12 col-md-8 offset-md-2">
        <b-form @submit.prevent="onSubmit">
          <b-form-group
            id="input-group-1"
            label="BattleTag:"
            label-for="input-text"
            description="Format: YourProfile#1234 for example: SuperRambo#2613"
          >
            <b-form-input
              v-focus
              id="input-text"
              v-model="form.battleTag"
              type="text"
              size="lg"
              required
              placeholder="BattleTag"
            />
          </b-form-group>

          <b-form-group id="input-group-3" label="Region:" label-for="input-region">
            <b-form-select
              id="input-region"
              v-model="form.region"
              size="lg"
              :options="regions"
              required
            />
          </b-form-group>

          <div class="d-flex justify-content-end mt-5">
            <b-button id="btn-diablo" type="submit" variant="primary" size="lg"
              >Search</b-button
            >
          </div>
        </b-form>
      </div>
    </div>
  </div>
</template>

<script>
import { regions } from '@/utils/regions'

export default {
  name: 'MainForm',
  data () {
    return {
      form: {
        battleTag: '',
        region: 'eu'
      }
    }
  },
  computed: {
    regions () {
      return regions.map((region) => ({ value: region, text: region.toUpperCase() }))
    }
  },
  methods: {
    onSubmit () {
      const { region, battleTag } = this.form
      this.$router.push({
        name: 'Profile',
        params: { region, battleTag: battleTag.replace('#', '-') }
      })
    }
  }
}
</script>
<style lang="stylus">
#btn-diablo{
  background-color: #2b0c00;
}
</style>
