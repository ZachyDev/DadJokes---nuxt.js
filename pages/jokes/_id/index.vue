<template>
<div>
    {{ $route.params.id }}
</div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
        return {
            joke: {}
        }
    },
    created() {
        const config = {
            headers: {
                Accept: 'application/json'
            }
        }
        axios.get(`https://icanhazdadjoke.com/j/${ this.$route.params.id }`, config)
            .then(res => {
                this.joke = res.data.joke;
                console.log(this.joke)
            })
            .catch(err => {
                console.log(err)
            })
    }
}
</script>

<style scoped>

</style>
