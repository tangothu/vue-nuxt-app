<template>
  <section class="section">
    <div class="columns">
      <button class="button is-primary is-medium"
        @click="launchLoginModal()">
        Launch login modal component
      </button>

      <div class="divider"/>

      <button class="button is-primary is-medium"
        @click="launchDatePickerModal()">
        Launch date picker modal component
      </button>

      {{ selected_date }}
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'
import ModalComponent from '~/components/ModalComponent'
import DatePickerModalComponent from '~/components/DatePickerModalComponent'

export default {
  name: 'HomePage',
  props: {
            selected_date: {
                type: Date,
                required: true
            },
        },

  components: {
    Card
  },

  methods: {
    launchLoginModal() {
            this.$modal.open({
                parent: this,
                component: ModalComponent,
                hasModalCard: true
            })
        },
    launchDatePickerModal() {
            let self = this;
            this.$modal.open({
                parent: this,
                component: DatePickerModalComponent,
                hasModalCard: true,
                events: {
                    modalChangeDate(value) {
                        self.selected_date = value;
                    }
                }
            })
        },
  }
}
</script>
<style lang="scss" scoped>
.divider{
    width:5px;
    height:auto;
    display:inline-block;
}
</style>