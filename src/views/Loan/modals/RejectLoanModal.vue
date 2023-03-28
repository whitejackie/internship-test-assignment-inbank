<template>
    <div
        id="modal-backdrop"
        class="absolute inset-0 w-full h-full flex justify-center items-center bg-white bg-opacity-40 backdrop-blur-lg"
    >
        <div
            id="modal"
            class="rounded-3xl flex flex-col justify-between modal-content justify-items-center"
        >
                <button
                    class="w-6 h-6"
                    @click="closeModal"
                >
                    <img src="@/img/close.svg" alt="close">
                </button>
                <div>
                    <h2 class="mb-2">{{ modalTitle }}</h2>
                    <p>{{ modalDescription }}</p>
                </div>
                <ul class="grid grid-cols-5">
                    <li v-for="option in options" class="mt-3 col-span-4 col-start-2 flex items-center">
                        <input id="modal-checkbox" class="w-5 h-5 mr-4" type="checkbox">
                        <label for="modal-checkbox">{{ option }}</label>
                    </li>
                </ul>
                <div>
                    <span class="flex justify-center">
                        <button
                            class="btn btn-primary btn-lg"
                            @click="closeModal"
                        >Cancel loan application</button>
                    </span>
                </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "RejectLoanModal",
    props: {
        modalActive: {
            type: Boolean,
            default: false,
        }
    },
    data() {
        return {
            isOpen: false,
            modalTitle: 'Help us improve',
            modalDescription: 'We want to offer our clients the best experience. Your feedback will help us get better. You can select multiple answers.',
            options: [
                'Loan amount is too small',
                'Interest is too high',
                'Contract fee is too high',
                'Not sure if I should take a loan',
                'I prefer another bank',
                'Timing is not right',
                'Other',
            ],
        }
    },
    methods: {
        closeModal() {
            this.$emit('close');
        }
    }

}
</script>

<style lang="css">
#modal {
    min-width: 505px;
    min-height: 667px;
    max-width: 505px;
    max-height: 667px;
    background: #FDFDFD;
    box-shadow: 0 4px 10px rgba(130, 130, 130, 0.25);
}

.modal-content {
    padding: 3rem 1.75rem
}
</style>