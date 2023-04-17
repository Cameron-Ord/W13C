<template>
        <div class="parent">
            <section class="section_main">
                <article>
                    <div class="main_span">

                        <span class="selection_span">
                            
                            <h3 class="song_title">{{ current.title }}</h3>
                        
                            <h3 class="song_artist">{{ current.artist }}</h3>

                            <img v-bind:src="current.image_url">
                        
                        
                        </span>
            
                        <span class="buttons_span">
                        <button class="prev">PREV</button>

                        <button class="play" v-if="!isPlaying" @click="play">PLAY</button>

                        <button class="pause" v-else @click="pause">PAUSE</button>

                        <button class="next">NEXT</button>
             
                        <p v-if="!isPlaying">pick a song</p>

                        <p v-else>now playing</p>

                    </span>
                    </div>

                </article>
                <article class="playlist">

                    <span class="playlist_span">

                    <h3>The Playlist</h3>

                    <button v-for="song in songs" :key="song.title" @click="play(song)" :class="(song.title == current.title) ? 'song_playing' : 'song'">{{ song.title }} - {{ song.artist }}  </button>

                </span>
               
              





                </article>
            </section>
        </div>
</template>

<script>
    export default {




        data() {
            return {


                current:{},

                index: 0,

                isPlaying: false,
          
                songs: [{


                    title: `Roller Mobster`,

                    artist: `Carpenter Brut`,

                    song_id: 7,

                    image_url: `https://m.media-amazon.com/images/I/51PHl1VZO3L._AC_SX342_.jpg`,

                    src: require(`../assets/roller-mobster.mp3`)

   



                },
                {

                    title: `Dimished to B`,

                    artist: `Necrophagist`,

                    song_id: 5,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/a/af/Epitaph_cover.jpg/220px-Epitaph_cover.jpg`,

                    src: require(`../assets/dimished-to-b.mp3`)
         


                },
                {
                    title: `Confine of Shadows`,

                    artist: `Disincarnate`,

                    song_id: 8,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/f/f9/Disincarnate.jpg`,

                    src: require(`../assets/confine-of-shadows.mp3`)

         


                },
                {

                    title: `The planet that once used to absorb flesh in order to achieve divinity and immortality(suffocated to the flesh it desired)`,

                    artist: `Demilich`,

                    song_id: 9,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/1/10/Nespithe.JPG/220px-Nespithe.JPG`,

                    src: require(`../assets/planet.mp3`)

                    



                },
                {

                    title: `Raining Steel`,

                    artist: `Perturbator`,

                    song_id: 10,

                    image_url: `https://i.scdn.co/image/3092c7fb063d40e02cb9c890dad854bd1e34fbfc`,

                    src: require(`../assets/raining-steel.mp3`)
                 


                },

            ],

            player: new Audio()

            }
        },

        methods: {

            play (song) {

                if(typeof song.src !== "undefined"){
                    this.current = song;

                
          
                    this.player.src = this.current.src;

                }
                this.player.play();
                this.isPlaying = true;
            },

            pause (){


                this.player.pause();
                this.isPlaying = false;
            },

            next(){

                

            },

            prev (){


            }
    

        },


        created() {

            this.current = this.songs[this.index];

            this.player.src =  this.current.src;


        }
    }
</script>

<style scoped>



.section_main{

    display: grid;

    align-items: center;

    justify-items: center;


}

.selection_span{

display: grid;

justify-items: center;

align-items: center;

grid-template-rows: 1fr 1fr 1fr;

text-align: center;

}

.selection_span>img{

    width: 100px;

margin-bottom: 20px;
}

.selection_span>h3{

  width: 100%;

}

.buttons_span{


    display: grid;

    justify-items: center;

    align-items: center;

    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;

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