<script>
    function generateDeck(){

        let deck = [];
        
        for(let i=1; i<10; i++){

            let card = {
                id: i,
                img:`char-${i}.png`,
            }
            //Hämtar korten 
            deck.push(card) 
        }
        return deck;
    }

    let show = false;
    let bomb = false;
    let score = 0;
    let result = "";
    
    function addOne(event) {
        score += 1;
        console.log(score);
    }

    function bomb(card, event){
        if (card.img =='char-9.png'){
            let result = score;
        }
    }

    let deck = generateDeck()


</script>

<main>
    <nav>
        <div class="score">Mina poäng: {score}</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
        <article class="card" on:click={addOne} on:click={bomb(card)}>
        <img class:show ={show} on:click="{() => show = !show}" src="img/{card.img}">
        </article>
        {/each}
    </div>
    
    <aside class="end">
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
            background-color: red;
        }

        .wrapper{
            background-color: gray;
            padding: 2rem;
            display: grid;
            grid-template-columns: repeat(3, 150px);
            gap: 1rem;
            align-items: center;

            article{
                .show{
                    opacity: 0;
                }

                img{
                    width: 100%;
                    opacity: 1;
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