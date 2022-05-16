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
    function shuffleArray(array) {
        for (var i = array.length - 1; i > 0; i--) {
            var j = Math.floor(Math.random() * (i + 1));
            var temp = array[i];
            array[i] = array[j];
            array[j] = temp;
        }
    }

    let deck = generateDeck()
    let new_deck = shuffleArray(deck);

    let lost = {
        end: false,
    }

    let show = false;
    let score = 0;
    let result = "";
    
    function addOne() {
        score += 1;
    }

    function bomb(card){ 
        deck[card.id-1].flipped=true;
        if (card.id == 9){
            let result = score;
            let end=true;
            console.log(result);
        }
    }



</script>

<main>
    <nav>
        <div class="score">Mina poäng: {score}</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
        <article class="card {card.flipped === true ? 'flipped' : ''}" on:click={addOne} on:click={bomb(card)}>
        <img class:show ={show} on:click="{() => show = !show}" src="img/{card.img}">
        </article>
        {/each}
    </div>
    
    <aside class= "{lost.end ===true ? 'end' : ''}" >
        <h1>You lost</h1>
        <h2>Your score: {result} </h2>
    </aside>

</main>

<style lang="scss">
    main{
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        aside{
            opacity: 0;
            .end{
                opacity: 1;
                background-color: red;
                width: 3rem;
                height: 50vh;
            }
        }

        .wrapper{
            background-color: gray;
            padding: 2rem;
            display: grid;
            grid-template-columns: repeat(3, 150px);
            gap: 1rem;
            align-items: center;

            article{
                &.flipped{
                    img{
                    opacity: 1;
                    border-style: solid;
                    }
                }

                img{
                    width: 100%;
                    opacity: 0;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex-direction: column;
                    border: 3px;
                    border-style: solid;
                    border-radius: 5px;
                    background-color: green;
                }
            }
            
        }
    }
</style>