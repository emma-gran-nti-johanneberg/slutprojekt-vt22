<script>
    function generateDeck(){

        let deck = [];
        
        for(let i=1; i<10; i++){
            let card = {
                id: i,
                flipped:false,
                img:`char-${i}.png`,
            }
            //Hämtar korten 
            deck.push(card) 
        }
        return deck;
    }

    /*Funktion för att blanda kortleken*/
    function shuffleArray(array, positions) {
        for (var i = array.length - 1; i > 0; i--) {
            var j = Math.floor(Math.random() * (i + 1));
            var temp = array[i];
            array[i] = array[j];
            array[j] = temp;
            positions[i] = j;
            positions[j] = i;
        }

        for(let i = 0; i < array.length; i++) {
            let id = array[i].id;
            positions[id] = i;
        }
    }

    let deck = generateDeck();
    let positions = {};
    let new_deck = shuffleArray(deck, positions);
    

    let score = 0;

    let state = {
        begin: "Nu kör vi!",
        alive: "Det där var ingen bomb, så fortsätt",
        bomb: "Det där däremot var en bomb, så nu är du död",        
    }
    
    function addOne() {
        score += 1;
        state.begin=state.alive;
    }

    function bomb(card, positions){ 
        if (card.id == 9){
            state.alive=state.bomb;
        }
        
        deck[positions[card.id]].flipped=true;
        console.log(card.id)
        console.log(card.img)
    }



</script>

<main>
    <nav>
        <div class="score">Mina poäng: {score}</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
            <article on:click={bomb(card, positions)}>
            <p>{card.id}</p>
            <img class="{card.flipped ? 'flipped' : ''}" on:click={addOne()} src="img/{card.img}">
            </article>
        {/each}
    </div>
    
    <aside>
        <h2>{state.begin}</h2>
    </aside>

</main>

<style lang="scss">
    main{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        aside{
            width: auto;
        }


        .wrapper{
            background-color: gray;
            padding: 2rem;
            display: grid;
            grid-template-columns: repeat(3, 125px);
            gap: 1rem;
            align-items: center;

            article{
                border-style: solid;
                border-radius: 5px;
                background-color: green;
                border: 3px;

                img.flipped{
                    opacity: 1;
                    border-style: solid;
                    border-radius: 5px;
                    background-color: green;
                }
                

                img{
                    width: 100%;
                    opacity: 0;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex-direction: column;
                }
            }
            
        }
    }
</style>