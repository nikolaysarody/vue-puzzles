<template>
    <div class="container">
        <div class="puzzle">
            <pre class="puzzle-text">{{currentPuzzle()}}</pre>
            <form @submit.prevent="check()">
                <input v-model="answer" class="puzzle-input-text" type="text" id="answer" placeholder="Ответ">
            </form>
            <button class="puzzle-button-left" @click="check()">Ответить</button>
            <button class="puzzle-button-right" @click="next()" v-if="numberOfPuzzle < 2">Вперед</button>
            <button class="puzzle-button-right" @click="next()" v-else disabled>Вперед</button>
            <button class="puzzle-button-right" @click="back()" v-if="numberOfPuzzle > 0">Назад</button>
            <button class="puzzle-button-right" @click="back()" v-else disabled>Назад</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Puzzle",
        data() {
            return {
                puzzle: [{
                    'text': 'Заплелись густые травы,\n' +
                        'Закудрявились луга,\n' +
                        'Да и сам я весь кудрявый,\n' +
                        'Даже завитком рога.',
                    'answers': ['баран', 'барашек']
                }, {
                    'text': 'У него огромный рот,\n' +
                        'Он зовется …',
                    'answers': ['бегемот', 'бегемотик']
                }, {
                    'text': 'Хожу в пушистой шубе,\n' +
                        'Живу в густом лесу.\n' +
                        'В дупле на старом дубе\n' +
                        'Орешки я грызу.',
                    'answers': ['белка', 'белочка']
                }],
                numberOfPuzzle: 0,
                answer: '',
                trueAnswer: 0,
                falseAnswer: 0,
            }
        },
        methods: {
            back() {
                this.numberOfPuzzle--;
            },
            next() {
                this.numberOfPuzzle++;
            },
            currentPuzzle() {
                return this.puzzle[this.numberOfPuzzle].text;
            },
            check() {
                for (let i = 0; i <= this.puzzle[this.numberOfPuzzle].answers.length - 1; i++) {
                    if (this.answer.toLowerCase() === this.puzzle[this.numberOfPuzzle].answers[i]) {
                        this.trueAnswer++;
                        alert('Вы абсолютно правы!\n' + 'Количество правильных ответов: ' + this.trueAnswer + '\n' + 'Количество ложных ответов: ' + this.falseAnswer);
                        return;
                    }
                }
                this.falseAnswer++;
                alert('Ваш ответ неверен\n' + 'Количество правильных ответов: ' + this.trueAnswer + '\n' + 'Количество ложных ответов: ' + this.falseAnswer);
            }
        }
    }
</script>

<style scoped lang="scss">
    .container {
        background-color: white;
        width: 60%;
        height: 60%;
        min-width: 400px;
        max-width: 500px;
        padding: 40px;
        overflow: auto;
        margin: auto;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        font-size: 18px;

        .puzzle {
            color: #05445e;

            .puzzle-text {
                height: 78px;
            }

            .puzzle-button-right {
                float: right;
                margin-left: 10px;
            }

            .puzzle-button-left, .puzzle-input-text {
                float: left;
            }

            .puzzle-input-text {
                line-height: 28px;
                margin-right: 10px;
                font-size: 16px;
            }

            .puzzle-button-right, .puzzle-button-left {
                cursor: pointer;
                line-height: 34px;
                border: 0;
                border-radius: 6px;
                font-weight: 300;
                color: #05445e;
                background-color: #D4F1F4;
                font-size: 16px;
            }
        }
    }
</style>