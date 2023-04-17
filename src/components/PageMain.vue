<template>
    <div class="parent">
        <section class="section_main">
            <article>
                <span class="main_span">

                    <button v-for="(song, counter) in songs" :key="counter" :post="song" @highlight_post="show_music">{{ song[`title`] }}</button>

                </span>
            </article>
        </section>
    </div>
</template>

<script>
    export default {

        methods:{

            show_music(post) {

                this.special_content = post[`title`];

            }


        },


        data() {
            return {



          
                songs: [{


                    title: `Roller Mobster`,

                    artist: `Carpenter Brut`,

                    song_id: 7,

                    image_url: `https://m.media-amazon.com/images/I/51PHl1VZO3L._AC_SX342_.jpg`

                },
                {

                    title: `Dimished to B`,

                    artist: `Necrophagist`,

                    song_id: 5,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/a/af/Epitaph_cover.jpg/220px-Epitaph_cover.jpg`


                },
                {
                    title: `Confine of Shadows`,

                    artist: `Disincarnate`,

                    song_id: `8`,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/f/f9/Disincarnate.jpg`


                },
                {

                    title: `The planet that once used to absorb flesh in order to achieve divinity and immortality(suffocated to the flesh it desired)`,

                    artist: `Demilich`,

                    song_id: `9`,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/1/10/Nespithe.JPG/220px-Nespithe.JPG`


                },
                {

                    title: `Raining Steel`,

                    artist: `Perturbator`,

                    song_id: `10`,

                    image_url: `https://i.scdn.co/image/3092c7fb063d40e02cb9c890dad854bd1e34fbfc`


                },

            ]

            }
        },
    }
</script>

<style scoped>

.section_main{

    display: grid;



    align-items: center;

    justify-items: center;


}


.main_span{

    display:grid;

    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;

    align-items: center;

    justify-items: center;
}

button{


    display: grid;

    width: 300px;

    align-items: center;


    justify-items: center;
}
</style>