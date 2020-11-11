<template>
    <div class="container">
        <pre v-for="(text, index) in texts" :key="texts[index]" @click="showText(index)">{{texts[index]}}</pre>
        <img class="img" src="../assets/cat.jpg" alt="котик" @click="modal = !modal">
        <div class="modal-mask" v-if="modal">
            <div class="modal-wrapper">
                <div class="modal-container">
                    <div class="modal-body">
                        <slot name="body">
                            <img class="img-modal" src="../assets/cat.jpg" alt="котик" @click="modal = !modal">
                        </slot>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Form",
        data() {
            return {
                texts: ['Заплелись густые травы,\n' +
                'Закудрявились луга,\n' +
                'Да и сам я весь кудрявый,\n' +
                'Даже завитком рога.',
                    'У него огромный рот,\n' +
                    'Он зовется …',
                    'Хожу в пушистой шубе,\n' +
                    'Живу в густом лесу.\n' +
                    'В дупле на старом дубе\n' +
                    'Орешки я грызу.'],
                modal: false,
            }
        },
        methods: {
            showText(i){
                alert(this.texts[i]);
            },
            showImg(){
                alert()
            }
        }
    }
</script>

<style scoped lang="scss">
    .container {
        background-color: white;
        padding: 40px;
        overflow: auto;
        margin: auto;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        font-size: 18px;

        pre {
            color: #05445e;
            cursor: pointer;
            margin-right: 55%;
        }

        .img {
            height: 50%;
            cursor: pointer;
        }
        .img-modal{
            max-width: 100%;
            max-height: 100%;
            overflow: auto;
            margin: auto;
            position: absolute;
            top: 0; left: 0; bottom: 0; right: 0;
            cursor: pointer;
        }

        .modal-mask {
            position: fixed;
            z-index: 9998;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: table;
            transition: opacity 0.3s ease;
        }
        .modal-wrapper {
            display: table-cell;
            vertical-align: middle;
        }
        .modal-container {
            max-width: 90%;
            max-height: 90%;
            padding: 20px 30px;
            background-color: #fff;
            border-radius: 2px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
            transition: all 0.3s ease;
            overflow: auto;
            margin: auto;
            position: absolute;
            top: 0; left: 0; bottom: 0; right: 0;
        }
        .modal-body {
            margin: 0 auto;
        }
        .modal-button {
            float: right;
        }
    }
</style>