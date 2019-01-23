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
                <button class="button is-primary" @click="changeDate();$parent.close();">Change Date</button>
            </footer>
        </div>
    </form>
</template>

<script>
    export default {
        props: {
            my_date: {
                type: Date,
                required: false
            },
        },
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