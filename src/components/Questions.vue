<template>

    <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{width: `${questionsAnswered / questions.length * 100}%`}"></div>
            <div class="status">{{questionsAnswered}} out of {{questions.length}} questions answered</div>
        </div>
        <div class="single-question" v-for="(question, i) in questions"
             :key="question.q" v-show="questionsAnswered === i">
            <div class="question">{{question.q}}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers"
                     :key="answer.text" @click.prevent="selectAnswer(answer.is_correct)">
                    {{answer.text}}
                </div>
            </div>
        </div>
    </div>

</template>

<script>
    export default {
        name: "QuestionsQ",
        props: {
            questions: Array,
            questionsAnswered: Number,
        },
        emits: ['question-answered'],
        methods: {
            selectAnswer(is_correct) {
                this.$emit('question-answered', is_correct)
            }
        }
    }
</script>

<style scoped>

</style>