<template>
        <div class="parent">
            <section class="section_main">
                <article>
                    <div class="main_span">

                        <span class="selection_span">
                            <!--displaying the selected title using a current variable-->
                            <h3 class="song_title">{{ current[`title`] }}</h3>
                        
                            <h3 class="song_artist">{{ current[`artist`] }}</h3>

                            <!--binding the image that is selected from the object inside the current variable-->
                            <img v-bind:src="current[`image_url`]">
                        
                        
                        </span>
            
                        <span class="buttons_span">
                            <!--Some buttons (prev and next do not work)-->
                        <button class="prev">PREV</button>
                        <!--an if statement that will show the play button only if isPlaying is set to false-->
                        <!--add event listener set to click to call the play() function-->
                        <button class="play" v-if="!isPlaying" @click="play">PLAY</button>
                        <!--if isPlaying === true, it will show a pause button that calls the pause function-->
                        <button class="pause" v-else @click="pause">PAUSE</button>

                        <button class="next">NEXT</button>
                        <!--if isPlaying is false, injects 'pick a song' p tag-->
             
                        <p v-if="!isPlaying">pick a song</p>
                        <!--if isPlaying = false, injects 'now playing'-->

                        <p v-else>now playing</p>

                    </span>
                    </div>

                </article>
                <article class="playlist">

                    <span class="playlist_span">

                    <h3>The Playlist</h3>
                    <!--the loop for the selection buttons-->

                    <!--clicking calls the play function-->

                    <!--the :class selects the song title and makes it equal to the current title-->
                    <button v-for="song in songs" :key="song[`title`]" @click="play(song)" :class="(song[`title`] == current[`title`])">{{ song[`title`] }} - {{ song[`artist`] }}  </button>

                </span>
               
              





                </article>
            </section>
        </div>
</template>

<script>
    export default {




        data() {
            return {

                //current variable to select and hold the song object//

                current:{},

                index: 0,

                //setting the isPlaying to false by default so that it only plays when you click the correct buttons//

                isPlaying: false,
          
                //the array of objects containing the key values//

                songs: [{


                    title: `Roller Mobster`,

                    artist: `Carpenter Brut`,

                    song_id: 7,

                    image_url: `https://m.media-amazon.com/images/I/51PHl1VZO3L._AC_SX342_.jpg`,

   

   



                },
                {

                    title: `Diminished to B`,

                    artist: `Necrophagist`,

                    song_id: 5,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/a/af/Epitaph_cover.jpg/220px-Epitaph_cover.jpg`,


         


                },
                {
                    title: `Confine of Shadows`,

                    artist: `Disincarnate`,

                    song_id: 8,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/f/f9/Disincarnate.jpg`,

    
         


                },
                {

                    title: `The planet that once used to absorb flesh in order to achieve divinity and immortality(suffocated to the flesh it desired)`,

                    artist: `Demilich`,

                    song_id: 9,

                    image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/1/10/Nespithe.JPG/220px-Nespithe.JPG`,

              
                    



                },
                {

                    title: `Raining Steel`,

                    artist: `Perturbator`,

                    song_id: 10,

                    image_url: `https://i.scdn.co/image/3092c7fb063d40e02cb9c890dad854bd1e34fbfc`,

                 


                },

            ],

         

            }
        },

        methods: {

            //methods containing the respective functions//

        
            play (song) {

                //if the song_id is not undefined, make current equal to the song object//

                if(typeof song[`song_id`] !== "undefined"){
                    this.current = song;

                
          

                }
           
                //setting the isPlaying variable to true on click//

                this.isPlaying = true;
            },

            pause (){


                //setting the isPlaying variable to false on click//

                this.isPlaying = false;
            },

            next(){

                

            },

            prev (){


            }
    

        },


        created() {

            //defining current before mount//

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