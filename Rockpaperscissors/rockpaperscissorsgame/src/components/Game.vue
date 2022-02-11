<template>
    <div class="container">
        <h1>Rock Paper Scissors</h1>
        <div class="score">
            <h2>{{this.playerScore}} - {{this.computerScore}} </h2>
        </div>
        <button type="button" class="btn btn-primary" v-on:click="selected = 'rock'">rock</button>
        <button type="button" class="btn btn-danger" v-on:click="selected = 'paper'">paper</button>
        <button type="button" class="btn btn-success" v-on:click="selected = 'scissors'">scissors</button>
        <button type="button" class="btn btn-secondary" v-on:click="play">computer plays</button>
            <p>your choice: {{ selected }}</p>
            <p>computer's choice: {{ computerSelected }}</p>
            <div>{{ result }}</div>
        </div>
</template> 


<script>
 const choices = ['rock', 'paper', 'scissors'];
 export default{
    name: "App",
     data(){
         return {
       selected: "",
       computerSelected: "",
       playerScore: 0,
       computerScore: 0
     }
    },
    computed: {
            result() {
            if (this.computerSelected === this.selected) {
                return `it's a tie`;
            } else {
                if ((this.computerSelected === "rock" && this.selected === "scissors") || (this.computerSelected === "paper" && this.selected === "rock") ||(this.computerSelected === "scissors" && this.selected === "paper")) {
                return "computer won";
                }
                return "player won";
                }
            },
        },
        methods: {
            play() {
                if (!this.selected) {
                    console.log("Make a choice");
                return 'Please select a choice';
            }
            const computerChoice = Math.floor(Math.random() * choices.length);
            this.computerSelected = choices[computerChoice];
            }
        }     
 };
</script>

