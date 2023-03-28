<template>
    <header>
        <nav class="mt-5 mb-12" :class="{blur: isModalVisible}">
            <div class="grid grid-cols-4 justify-items-center">
                <div class="col-span-2 col-start-2">
                    <img src="@/img/inbank-logo.svg" alt="Logo">
                </div>
                <div class="flex justify-items-end items-center">
                    <a><img src="@/img/side-menu.svg" alt="Side-menu"></a>
                </div>
            </div>
        </nav>
    </header>
    <div :class="{blur: isModalVisible}">
        <div class="content grid grid-cols-2">
            <div class="banner-container flex justify-end">
                <img class="banner" src="@/img/banner.png" alt="banner">
            </div>
            <div class="loan-container grid grid-cols-1 divide-y justify-center">
                <div class="flex flex-col items-center justify-center">
                    <h1 class="mb-1">Good news!</h1>
                    <p>Your loan has been approved.</p>
                </div>
                <div class="flex flex-col items-center justify-center">
                    <ul>
                       <li class="grid grid-cols-2 gap-x-4" v-for="(value, propertyName) in offer">
                           <div class="flex justify-end">
                               <h4>
                                   {{ propertyName }}
                               </h4>
                           </div>
                           <h3>
                               {{ value }}
                           </h3>
                       </li>
                    </ul>
                </div>
                <div class="flex flex-col items-center justify-center">
                    <ul>
                        <li class="grid grid-cols-2 gap-x-4" v-for="(value, propertyName) in percents">
                            <div class="flex justify-end">
                                <h4>
                                    {{ propertyName }}
                                </h4>
                            </div>
                            <h3>
                                {{ value }}
                            </h3>
                        </li>
                    </ul>
                </div>
                <div class="flex flex-col items-center justify-center">
                    <div class="flex">
                        <img src="@/img/check-circle.svg" alt="check">
                        <p class="pl-2">Promo code applied</p>
                    </div>
                </div>
                <div class="flex flex-col items-center justify-center">
                    <button
                        class="btn btn-primary btn-lg"
                        type="button"
                    >
                        View offer details
                    </button>
                    <button
                        class="mt-3 btn-secondary"
                        type="button"
                        @click="showModal"
                    >
                        Not interested
                    </button>
                </div>
            </div>
        </div>
    </div>
    <RejectLoanModal
        v-show="isModalVisible"
        @close="closeModal"
    />
</template>

<script>
import RejectLoanModal from "@/views/Loan/modals/RejectLoanModal.vue";

export default {
    components: {
        RejectLoanModal
    },
    data() {
        return {
            isModalVisible: false,
            offer: {
                'Personal loan offer': '1,700.00 €',
                'Loan period': '36 months',
                'Monthly payment': '95.27 €',
            },
            percents: {
                'Interest rate': '12.90%',
                'Margin': '8.90% + 6 months EURIBOR (0%)'
            },
        };
    },
    methods: {
        showModal() {
            this.isModalVisible = true;
        },
        closeModal() {
            this.isModalVisible = false;
        }
    }
}
</script>

<style lang="css" scoped>
.blur {
    filter: blur(10px);
}

.banner {
    border-radius: 1.25rem;
    box-shadow: -30px -30px 0 rgb(248, 245, 252);
}

.divide-y {
    max-width: 470px;
    margin-left: 45px;
}

.loan-container .flex-col {
    padding-top: 15px;
    padding-bottom: 15px
}
</style>