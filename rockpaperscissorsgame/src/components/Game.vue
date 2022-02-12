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

            <div class="d-flex justify-content-center">
                <button  class="button" v-on:click="play">Play</button>
                <button class="button" v-on:click="restart">Restart the game</button>
            </div>
        </div>
        
        <div class="container">
            <div class="row">
                <h4>your choice: <span>{{ selected }}</span></h4>
                <h4>computer's choice: <span>{{ computerSelected  }}</span></h4>
                <h3>{{this.resultaat}}</h3>
                <h5> {{this.errors}} </h5>
            </div>
        </div>
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
        errors: "",
        resultaat: "",
        playerScore: 0,
        computerScore: 0
        }
            },
            methods: {
                play() {
                    if (this.selected) {
                        const computerChoice = Math.floor(Math.random() * choices.length);
                        this.computerSelected = computerChoice
                        switch (this.computerSelected ) {
                            case 0:
                                this.computerSelected  = 'rock'
                            break;
                            case 1:
                                this.computerSelected  = 'paper'
                            break;
                            case 2:
                                this.computerSelected  = 'scissors'
                            break;
                        }
                        console.log('computer keuze:',this.computerSelected )
                            this.clash();
                        return this.computerSelected 
                    }
                    return this.errors = 'selecteer een keuze';
                },
                clash(){
                    if (this.computerSelected === this.selected) {
                        return this.resultaat = `it's a tie`;
                    } else {
                        if (
                        (this.computerSelected === "rock" && this.selected === "scissors") || (this.computerSelected === "paper" && this.selected === "rock") || (this.computerSelected === "scissors" && this.selected === "paper")) {
                            this.computerScore++;
                            return this.resultaat =  "computer won";
                        }
                            this.playerScore++;
                            return this.resultaat =  "player won";
                    }          
                },
                restart(){
                    this.playerScore = 0;
                    this.computerScore = 0;
                    this.selected = "";
                    this.computerSelected = "";
                    this.resultaat = "";
                }
    }
 };
</script>

