<script>
    function generateDeck(){

        let deck = [];
        
        for(let i=1; i<10; i++){

            let card = {
                id: i,
                img: `char-${i}.png`,
                bomb: false,
                hidden: true,
            }
            //Hämtar korten 
            deck.push(card) 
        }
        return deck;
    }

    let deck = generateDeck()


</script>

<main>
    <nav>
        <div class="time">Tiden ska stå här</div>
        <div class="score">Här kommer poängen att stå</div> 
    </nav>
    <div class="wrapper">
        {#each deck as card}
        <article class="card">
        <img src="img/{card.img}">
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

            img{
                width: 100%;
                opacity: 1;
                background-color: green;
                display: flex;
                justify-content: center;
                align-items: center;
                flex-direction: column;

                .hidden{
                    opacity: 0;
                }
            }
            
        }
    }
</style>