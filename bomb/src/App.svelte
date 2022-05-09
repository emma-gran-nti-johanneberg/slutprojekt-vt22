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
    
    function addOne(event) {
        score += 1
    }

    function flipp(event){
        show= !show
    }

    let deck = generateDeck()


</script>

<main>
    <nav>
        <div class="time">Tiden ska stå här </div>
        <div class="score">Här kommer poängen att stå {score}</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
        <article class="card" on:click={addOne}>
        <img classid="show" src="img/{card.img}" on:click={flipp}>
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
                border-color: red;
                background-color: green;

                img{
                    width: 100%;
                    opacity: 0;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    flex-direction: column;

                    .show{
                        opacity: 1;
                    }
                }
            }

            
            
        }
    }
</style>