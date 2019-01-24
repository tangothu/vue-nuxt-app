<template>
    <form class="modal-component">
        <div class="modal-card" style="width: auto">
            <header class="modal-card-head">
                <p class="modal-card-title">Choose date</p>
            </header>
            <section class="modal-card-body">
                <b-datepicker
                    v-model="my_date"
                    placeholder="Type or select a date..."
                    icon="calendar-today"
                    editable>
                </b-datepicker>
            </section>
            <footer class="modal-card-foot">
                <button class="button" type="button" @click="$parent.close()">Cancel</button>
                <button class="button is-primary" @click.prevent="changeDate();$parent.close();">
                    <!--This .prevent is needed so as not to re-render the entire parent page! -->
                    Change Date
                </button>
            </footer>
        </div>
    </form>
</template>

<script>
    export default {
        data: function () {
            return {
              my_date: new Date(),
            }
          },
        // No need to use my_date as prop here, as this prop is not passed from parent
        // otherwise will see [Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders.
        // Instead, use a data or computed property based on the prop's value. Prop being mutated: "my_date"

        methods: {
            changeDate() {
                this.$emit('modalChangeDate', this.my_date);
            }
        }

    }
</script>
<style lang="scss" scoped>
.modal .animation-content .modal-card {
    overflow: visible !important;
}
.modal-card-body {
    overflow: visible !important;
}
</style>