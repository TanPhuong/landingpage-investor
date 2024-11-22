<script setup>
const props = defineProps({
  mobileView: {
    type: Boolean,
    required: true
  }
})
</script>

<template>
    <main>
        <div class="modal fade" id="backdropLetter" data-bs-keyboard="false" tabindex="-1"
            aria-labelledby="backdropLetterLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content">
                    <div class="modal-body d-flex justify-content-around">
                            <div class="img-section w-50" v-if="!props.mobileView">
                                <img src="../assets/images/Pop-up.png" alt="" class="w-100 block">
                            </div>

                            <div class="letter_container w-50">
                                <div class="title aver-semi-bold">Kính gửi: Quý nhà đầu tư !</div>

                                <div class="text">
                                    Đầu tiên, Ban Giám Đốc Công ty Cổ phần Thương mại và Dịch vụ du lịch
                                </div>
                            </div>
                    </div>
                </div>
                </div>

        </div>
    </main>
</template>

<style scoped>
.modal-dialog {
    max-width: max-content;

    & .modal-content {
        max-width: 1175px;
        padding: 32px; 
        border-radius: 32px;
    }

    & .modal-header {
        border-bottom: none;
    }

    & .modal-header, .modal-body {
        padding: 0;
    }
}

.img-section img {
    border-radius: 16px;
    height: -webkit-fill-available;
}

.form_container {
    width: 40%;
    max-width: 600px;
    background-color: #fff;
    border-radius: 10px;
    margin-left: 40px;

}
</style>
