<template>
    <div class="parent">
        <section class="section_main">
            <article>
                <span class="main_span">

                    <h2 class="song_title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
            
                    <button class="prev">PREV</button>

                    <button class="pause" @click="pause">PAUSE</button>
                    <button class="next">NEXT</button>
             
                    <p v-if="!isPlaying">pick a song</p>
                    <p v-else>now playing</p>
                </span>

            </article>
            <article class="playlist">
                <h3>The Playlist</h3>

                <button v-for="song in songs" :key="song.title" @click="play(song)" :class="(song.title == current.title)">{{ song.title }} - {{ song.artist }} </button>


               
              





            </article>
        </section>
    </div>
</template>

<script>
    export default {




        data() {
            return {

                isPlaying: false,

                index: 0,

                current:{},
          
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

                    song_id: 8,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/f/f9/Disincarnate.jpg`


                },
                {

                    title: `The planet that once used to absorb flesh in order to achieve divinity and immortality(suffocated to the flesh it desired)`,

                    artist: `Demilich`,

                    song_id: 9,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/1/10/Nespithe.JPG/220px-Nespithe.JPG`


                },
                {

                    title: `Raining Steel`,

                    artist: `Perturbator`,

                    song_id: 10,

                    image_url: `https://i.scdn.co/image/3092c7fb063d40e02cb9c890dad854bd1e34fbfc`


                },

            ]

            }
        },

        methods: {

            play (song) {

                if(typeof song.title != undefined){
                    this.current = song;

                

                }

                this.isPlaying = true;
            },

            pause (){


                this.isPlaying = false;
            }

            
    

        },


        created() {

            this.current = this.songs[this.index];


        }
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