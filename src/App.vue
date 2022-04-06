<template>

    <!--<CustomForm>
        <template v-slot:help>
            <p>This is some help text.</p>
        </template>
        <template v-slot:fields>
            <label>
                <input type="text" placeholder="name">
            </label>
            <label>
                <input type="text" placeholder="message">
            </label>
            <label>
                <input type="text" placeholder="Password">
            </label>
        </template>
        <template v-slot:buttons>
            <button type="submit">Submit</button>
        </template>
    </CustomForm>
    <CustomForm></CustomForm>-->
    <!--    <button type="button" @click="flag = !flag">Toggle</button>-->
    <!--<transition name="fade" mode="out-in">
        <h2 v-if="flag">Hello world</h2>
        <h2 v-else>Another hello</h2>
    </transition>-->

    <!-- <transition name="zoom">
         <h2 v-if="flag">Hello</h2>
     </transition>-->

    <div class="ctr">

        <QuestionsQ v-if="questionsAnswered < questions.length"
                    :questions="questions"
                    :questionsAnswered="questionsAnswered"
                    @question-answered="questionAnswered"/>
        <ResultQuestions v-else
                         :results="results"
                         :totalCorrect="totalCorrect"/>

        <button type="button" class="reset-btn" @click.prevent="reset"
                v-if="questionsAnswered === questions.length">
            Reset
        </button>

    </div>

</template>

<script>

    import QuestionsQ from "@/components/Questions";
    import ResultQuestions from "@/components/ResultQuestions";


    export default {
        name: 'App',
        components: {ResultQuestions, QuestionsQ},
        data() {
            return {
                questionsAnswered: 0,
                totalCorrect: 0,
                questions: [
                    {
                        q: 'What is 2 + 2?',
                        answers: [
                            {
                                text: '4',
                                is_correct: true
                            },
                            {
                                text: '3',
                                is_correct: false
                            },
                            {
                                text: 'Fish',
                                is_correct: false
                            },
                            {
                                text: '5',
                                is_correct: false
                            }
                        ]
                    },
                    {
                        q: 'How many letters are in the word "Banana"?',
                        answers: [
                            {
                                text: '5',
                                is_correct: false
                            },
                            {
                                text: '7',
                                is_correct: false
                            },
                            {
                                text: '6',
                                is_correct: true
                            },
                            {
                                text: '12',
                                is_correct: false
                            }
                        ]
                    },
                    {
                        q: 'Find the missing letter: C_ke',
                        answers: [
                            {
                                text: 'e',
                                is_correct: false
                            },
                            {
                                text: 'a',
                                is_correct: true
                            },
                            {
                                text: 'i',
                                is_correct: false
                            }
                        ]
                    },
                ],
                results: [
                    {
                        min: 0,
                        max: 2,
                        title: "Try again!",
                        desc: "Do a little more studying and you may succeed!"
                    },
                    {
                        min: 3,
                        max: 3,
                        title: "Wow, you're a genius!",
                        desc: "Studying has definitely paid off for you!"
                    }
                ]
                /*flag: false,*/
            }
        },
        methods: {
            questionAnswered(is_correct) {
                if (is_correct) {
                    this.totalCorrect++;
                }
                this.questionsAnswered++;
            },
            reset() {
                this.questionsAnswered = 0;
                this.totalCorrect = 0;
            }
        }
    }
</script>

<style>


    .fade-enter-from {
        opacity: 0;
    }

    .fade-enter-active {
        transition: all 1s linear;
    }

    .fade-leave-to {
        transition: all 1s linear;
        opacity: 0;
    }

    .zoom-enter-active {
        animation: zoom-in 1s linear forwards;
    }

    .zoom-leave-active {
        animation: zoom-out 1s linear forwards;
    }

    @keyframes zoom-in {
        from {
            transform: scale(0, 0);
        }
        to {
            transform: scale(1, 1);
        }
    }

    @keyframes zoom-out {
        from {
            transform: scale(1, 1);
        }
        to {
            transform: scale(0, 0);
        }
    }
</style>

