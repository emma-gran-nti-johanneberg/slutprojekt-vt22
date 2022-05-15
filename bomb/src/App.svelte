<script>
    function generateDeck(){

        let deck = [];
        
        for(let i=1; i<10; i++){

            let card = {
                id: i,
                img: `char-${i}.png`,
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
        score += 1
    }

    function bomb(card){
        if (card.id == 9){
            let result = score;
        }
    }

    function flipp(event){
        show= !show
    }

    let deck = generateDeck()


</script>

<main>
    <nav>
        <div class="score">Mina poäng: {score}</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
        <article class="card" on:click={addOne}>
        <img class="show" src="img/{card.img}" on:click={flipp}>
        </article>
        {/each}
    </div>
</main>

<style lang="scss">
    main{
        height: 75vh;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        nav {
            margin: 2rem;
        }

        .wrapper{
            background-color: gray;
            padding: 3rem;
            display: grid;
            grid-template-columns: repeat(3, 150px);
            gap: 1rem;
            align-items: center;

            article{
                

                img{
                    width: 100%;
                    opacity: 0;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex-direction: column;
                    border-color: red;
                    background-color: green;

                    .show{
                        opacity: 1;
                    }
                }
            }

            
            
        }
    }
</style>