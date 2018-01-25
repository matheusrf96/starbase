<template>
    <div id="app" class="container">
        <h3>{{title}}</h3>
        <div class="row">
            <Character 
                v-for="(id, index) in initial_ids"
                v-bind:id="id"
            />
        </div>        
    </div>
</template>

<script>
    import Character from './components/Character.vue'

    export default {
        name: 'app',
        data(){
            return {
                title: "Generate your team",
                initial_ids: [1, 5, 14]
            }
        },
        components: {
            Character
        }
    }
</script>
