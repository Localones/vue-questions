<template>
    <div class="result">
        <div class="title">{{results[resultIndex].title}}</div>
        <div class="desc">
            {{results[resultIndex].desc}}
        </div>
    </div>
</template>

<script>
    export default {
        name: "ResultQuestions",
        props: {
            results: Array,
            totalCorrect: Number,
        },
        computed: {
            resultIndex() {
                let index = 0;

                this.results.forEach((el, i) => {
                    if (el.min <= this.totalCorrect && el.max >= this.totalCorrect) {
                        index = i;
                    }
                })

                return index;
            }
        }
    }
</script>

<style scoped>

</style>