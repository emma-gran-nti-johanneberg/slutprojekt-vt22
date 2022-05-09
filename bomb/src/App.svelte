<script>
    function generateDeck(){

        let deck = [];

        for(i=1; i<10; i++){

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

    
function updateUI(){

document.querySelector('main').innerHTML = '';

    // loopa igenom våra kort
    deck.forEach(card => {
    
        let neutral = "";
        if(card.neutral){
            neutral = "neutral";
        }

        let el = `<article data-id="${card.id}" class="${neutral}">
            <img src="img/${card.img}" alt="card">
            </article>`;

        document
        .querySelector('main')
        .insertAdjacentHTML('beforeend', el);

    })
// generera HTML för varje kort

// Lyssna på klick på varje kort

}
</script>

<main>
    <div class="time">Tiden ska stå här</div>
    <div class="score">Här kommer poängen att stå</div>
    <div class="wrapper">

    </div>
</main>

<style lang="scss">
	
</style>