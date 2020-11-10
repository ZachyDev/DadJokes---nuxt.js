<template>
<div>
    <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" />
</div>
</template>

<script>
import axios from 'axios';
import Joke from '@/components/Joke.vue';
export default {
    data() {
        return {
            jokes: [],
        }
    },
    components: {
        Joke
    },
    created() {
        const config = {
            headers: {
                'Accept': 'application/json'
            }
        }
        axios.get('https://icanhazdadjoke.com/search', config)
            .then(res => {
                this.jokes = res.data.results;
            })
            .catch(err => {
                console.log(err)
            })
    },
    head() {
        return {
            title: "Dad Jokes",
            meta: [{
                hid: "description",
                name: "description",
                content: "Best place to get DadJokes"
            }]
        }
    }

}
</script>

<style lang="scss" scoped>

</style>
