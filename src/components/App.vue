<template>
    <div class="col-md-12">
        <h1>Got Jokes?</h1>
        <button class="btn btn-primary" @click="initJokes">Get A Ten Random Jokes</button>
        <button class="btn btn-primary" @click="addJoke">Get A Random Joke</button>
        <br>
            <span
                v-for="(type, index) in jokeTypes"
                :key="index"
            >
                <input 
                    type="checkbox" 
                    :value="type"
                    v-model="checkedJoke"
                >
                <label>
                    {{ type.toUpperCase() }}
                </label>&nbsp;
            </span>
        <br>
        <div class="col-md-12">
            <Jokes 
                v-for="(joke, index) in $store.state.jokes"
                v-show="checkedJoke.includes(joke.type)"
                :key="index"
                :joke="joke"
                :index="index"
            />
        </div>
    </div>
</template>

<script>
import { mapActions } from 'vuex';
import Jokes from './Jokes.vue';

export default {
    data() {
        return {
            jokeTypes: ['general', 'knock-knock', 'programming'],
            checkedJoke: ['general', 'knock-knock', 'programming']
        }
    },
    methods: mapActions([
        'initJokes', 'addJoke'
    ]),
    components: {
        Jokes
    }
}
</script>
