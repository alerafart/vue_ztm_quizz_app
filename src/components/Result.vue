<template>
    <div class="result">
        <div class="title">{{ results[resultIndex].title }}</div>
        <div class="desc">
            {{ results[resultIndex].desc }}
        </div>
    </div>
</template>

<script>

export default {
    props: ["results", "totalCorrect"],
    computed: {
        resultIndex() {
            let index = 0;

            // checks if total correct is above the min and below the max
            // it only executes if the results or totalcorrect properties  update
            // if a user enters an incorrect answer this function wont run again
            // saving ressources
            this.results.forEach((e, i) =>  {
                if(e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
                    index = i;
                }
            })
            return index;
        }
    }
};

</script>
