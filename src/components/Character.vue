<template>
    <div class="col-md-4" @click="switchCharacter">
        <div class="character-card">
            <div class="card-block">
                <h4 class="card-title"><b>{{character.name}}</b></h4>
                <p class="card-text">Birth Year: {{character.birth_year}}</p>
                <p class="card-text">Gender: {{character.gender}}</p>
                <p class="card-text">Height: {{character.height}}cm</p>
                <p class="card-text">Mass: {{character.mass}}kg</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['id'],
        data(){
            return {
                character: {}
            }
        },
        methods: {
            fetchCharacter(id){
                fetch(`https://swapi.co/api/people/${id}`, {
                    method: "GET"
                })
                    .then(response => response.json())
                    .then(json => this.character = json)
            },
            switchCharacter(){
                let random_id = Math.floor(Math.random() * 83) + 1
                this.fetchCharacter(random_id)
            }
        },
        created(){
            this.fetchCharacter(this.id)
        }
    }
</script>
