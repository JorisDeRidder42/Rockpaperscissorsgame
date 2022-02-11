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

