<template>
  <section class="section">
    <div class="columns">

      <button class="button is-primary is-medium"
        @click="launchDatePickerModal()">
        Launch date picker modal component
      </button>

    </div>
      <br>
    <div class="columns">
      <b-field>Date selected:</b-field>
        <div class="divider"/>
      <b-datepicker
            v-model="selected_date"
            icon="today"
            placeholder="DD-MMM-YYYY"
            :date-formatter="dateFormatter">
        </b-datepicker>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'
import ModalComponent from '~/components/ModalComponent'
import DatePickerModalComponent from '~/components/DatePickerModalComponent'

export default {
  name: 'HomePage',
  data: function () {
    return {
      selected_date: new Date(),
    }
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
                parent: self,
                component: DatePickerModalComponent,
                hasModalCard: true,
                events: {
                    modalChangeDate(value) {
                        self.selected_date = value;
                    }
                }
            })
        },
    dateFormatter(dt){
        let dateoptions = { year: 'numeric', month: 'short', day: 'numeric' };
        return dt.toLocaleDateString('en-GB', dateoptions);
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