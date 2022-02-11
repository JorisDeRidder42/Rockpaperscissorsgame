<template>
    <div class="container">
        <h1 class="text-center mt-5">Rock Paper Scissors</h1>
          <h4 class="text-center mb-3">Try your luck</h4>
        <div class="row">
            <div class="col-md-6">
                <div class="card">
                    <div class="card-body">
                        <div class="text-center score">
                            <h2>Player: {{this.playerScore}}</h2>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-md-6">
                <div class="card">
                    <div class="card-body">
                        <div class="text-center score">
                            <h2>Computer: {{this.computerScore}}</h2>
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div class="container">
            <div class="d-flex justify-content-center mt-5">
                <button class="button" v-on:click="selected = 'rock'">Rock</button>
                <button  class="button" v-on:click="selected = 'paper'">Paper</button>
                <button  class="button" v-on:click="selected = 'scissors'">Scissors</button>
            </div>
            <!-- <button type="button" class="btn btn" v-on:click="play">computer plays</button> -->
        </div>
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
                this.play();
                this.score();
                this.checkScore();
                return ''
            }
        },
        methods: {
            play() {
            const computerChoice = Math.floor(Math.random() * choices.length);
            this.computerSelected = choices[computerChoice];
            },
            score(){
                if (this.computerSelected === this.selected) { 
                    return "it's a tie";
                } else {
                 this.play();
                if ((this.computerSelected === "rock" && this.selected === "scissors") || (this.computerSelected === "paper" && this.selected === "rock") ||(this.computerSelected === "scissors" && this.selected === "paper")) {
                 this.checkScore();
                    this.computerScore++;
                return "computer won";
                }
                 this.checkScore();
                 this.playerScore++;
                return "player won";
                }
            },
            checkScore(){
                if (this.playerScore === 5) {
                    return "Player won"
                }
                else if(this.computerScore === 5)
                    return "computer won"
            }
        }     
 };
</script>

