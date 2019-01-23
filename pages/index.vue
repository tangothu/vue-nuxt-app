<template>
  <section class="section">
    <div class="columns is-mobile">

      <button class="button is-primary is-medium"
            @click="launchLoginModal()">
            Launch login modal component
        </button>

    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'
import ModalComponent from '~/components/ModalComponent'

export default {
  name: 'HomePage',

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
            }
  }
}
</script>
