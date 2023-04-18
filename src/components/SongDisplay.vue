<template>
    <div class="parent">
        <section class="section_main">
            <article class="main_article">
                <div class="main_span">

                    <div class="pick_song">
                        <p v-if="!isPlaying">pick a song</p>
                        <p v-else>now playing</p>
                        <!--if isPlaying = true, injects 'now playing'-->
                    </div>
                    <div v-if="isPlaying" class="selection_span">

                        <span>
                            <!--displaying the selected title using a current variable-->

                            <h3 v-if="isPlaying" class="song_title">{{ current[`title`] }}</h3>

                            <h3 v-if="isPlaying" class="song_artist">{{ current[`artist`] }}</h3>

                            <!--binding the image that is selected from the object inside the current variable-->

                            <img v-if="isPlaying" v-bind:src="current[`image_url`]">

                        </span>
                    </div>

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


                    </span>

                </div>

            </article>

            <article class="playlist">

                <span class="playlist_span">

                    <h3>The Playlist</h3>

                    <!--the loop for the selection buttons-->

                    <!--clicking calls the play function-->

                    <!--the :class selects the song title and makes it equal to the current title-->

                    <button class="overflow" v-for="song in songs" :key="song[`title`]" @click="play(song)"
                        :class="(song[`title`] == current[`title`])">{{ song[`title`] }} - {{ song[`artist`] }} </button>

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

            current: {},

            index: 0,

            //setting the isPlaying to false by default so that it only plays when you click the correct buttons//

            isPlaying: false,

            //the array of objects containing the key values//

            songs: [{


                title: `Roller Mobster`,

                artist: `Carpenter Brut`,

                song_id: 1,

                image_url: `https://m.media-amazon.com/images/I/51PHl1VZO3L._AC_SX342_.jpg`,

                src: require(`../assets/roller-mobster.mp3`)





            },
            {

                title: `Diminished to B`,

                artist: `Necrophagist`,

                song_id: 2,

                image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/a/af/Epitaph_cover.jpg/220px-Epitaph_cover.jpg`,

                src: require(`../assets/dimished-to-b.mp3`)



            },
            {
                title: `Confine of Shadows`,

                artist: `Disincarnate`,

                song_id: 3,

                image_url: `https://upload.wikimedia.org/wikipedia/en/f/f9/Disincarnate.jpg`,

                src: require(`../assets/confine-of-shadows.mp3`)



            },


            {
                title: `Glory to the Light of the Nation`,

                artist: `Tommy '86`,

                song_id: 4,

                image_url: `https://i.scdn.co/image/ab67616d0000b273fc3cf8e01cf47a8e15cdbdc8`,

                src: require(`../assets/glory.mp3`)

            },


            {

                title: `The planet that once used to absorb flesh in order to achieve divinity and immortality(suffocated to the flesh it desired)`,

                artist: `Demilich`,

                song_id: 5,

                image_url: `https://upload.wikimedia.org/wikipedia/en/thumb/1/10/Nespithe.JPG/220px-Nespithe.JPG`,

                src: require(`../assets/planet.mp3`)




            },
            {

                title: `Raining Steel`,

                artist: `Perturbator`,

                song_id: 6,

                image_url: `https://i.scdn.co/image/3092c7fb063d40e02cb9c890dad854bd1e34fbfc`,

                src: require(`../assets/raining-steel.mp3`)




            },

            ],

            //variable for audio//
            player: new Audio()

        }
    },

    methods: {


        play(song) {

            //if the song.src is not undefined, make current equal to the song object//

            
            if (song[`src`] !== undefined) {

                this.current = song;

                //making the player.src = current.src after mount inside the function//

                this.player.src = this.current.src;


                




            }

            this.player.play();

            //setting the isPlaying variable to true on click//

            this.isPlaying = true;



        },

        //methods containing the respective functions//

        pause() {


            //setting the isPlaying variable to false on click//

            this.player.pause();
            this.isPlaying = false;

        },


        next() {



        },

        prev() {


        }


    },


    created() {

        //defining current before mount, this gives the index for the case of using next/prev buttons//

        this.current = this.songs[this.index];

        //making the player.src equal to the current.src//
        this.player.src = this.current.src;


    }
}
</script>

<style scoped>
.parent{

    display: grid;

    width: 100%;

    justify-items: center;

    align-items: center;

    color: #31393C;
}

.parent>.section_main{

    display: grid;

    justify-items: center;

    align-items: center;

    width: 100%;

}

.parent>.section_main>.main_article{

    width: 100%;

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

 
}

.parent>.section_main>.main_article>.main_span{




    width: 100%;

    display: grid;

    justify-items: center;

    align-items: center;

}

.parent>.section_main>.main_article>.main_span>.pick_song{

display: grid;

grid-template-rows: 1fr;

margin-top: 25px;

width: 75%;

}
.parent>.section_main>.main_article>.main_span>.pick_song>p{

    padding: 25px;

    background-color: #F79824;

    border-radius: 25px;

    font-size: 2em;


}

.parent>.section_main>.main_article>.main_span>.selection_span{

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    width: 100%;

  

}

.parent>.section_main>.main_article>.main_span>.selection_span>span{

display: grid;

justify-items: center;

align-items: center;

text-align: center;

width: 80%;



background-color: #F79824;

border-radius: 50px;

margin-top: 25px;

margin-bottom: 25px;

grid-template-rows: 0.7fr 5vh 1fr;
}

.selection_span>span>h3{


    width:  90%;
}
.selection_span>span>img{

    height: 75%;
    width: 75%;
    border-radius: 25px;
    margin-top: 50px;
    margin-bottom: 50px;
}

.parent>.section_main>.main_article>.main_span>.buttons_span{

    width: 80%;

    grid-template-rows: 30px 30px 30px;

    display: grid;

    justify-items: center;

    align-items: center;

    text-align: center;

    margin-top: 25px;

    margin-bottom: 25px;

    background-color: #F79824;

    padding-top: 25px;

    padding-bottom: 25px;

    border-radius: 50px;
}  

.parent>.section_main>.main_article>.main_span>.buttons_span>button{


    width: 70%;

    display: grid;


    justify-items: center;


    align-items: center;


    text-align: center;

}
.parent>.section_main>.playlist{
    width: 100%;

    display: grid;

    justify-items: center;

    align-items: center;
}

.parent>.section_main>.playlist>.playlist_span{

    display: grid;

    justify-items: center;

    align-items: center;

    width: 80%;

    margin-top: 25px;

    margin-bottom: 25px;

    background-color: #F79824;

    padding-top: 25px;

    padding-bottom: 25px;

    border-radius: 50px;

    text-overflow: ellipsis;


  

}

.parent>.section_main>.playlist>.playlist_span>button{

display: grid;

justify-items: center;

align-items: center;

width: 70%;

}

.overflow{


    text-overflow: ellipsis;
}


@media only screen and (min-width: 700px){

    .parent{

}

.parent>.section_main{

    grid-template-columns: 1fr 1fr;

}

.parent>.section_main>.main_article{






}

.parent>.section_main>.main_article>.main_span{








}

.parent>.section_main>.main_article>.main_span>.pick_song{


    width: 60%;

}
.parent>.section_main>.main_article>.main_span>.pick_song>p{



}

.parent>.section_main>.main_article>.main_span>.selection_span{

}

.parent>.section_main>.main_article>.main_span>.selection_span>span{


width: 60%;

}

.selection_span>span>h3{


}
.selection_span>span>img{


    width: 35%;
}

.parent>.section_main>.main_article>.main_span>.buttons_span{


    width: 60%;
}  

.parent>.section_main>.main_article>.main_span>.buttons_span>button{



}
.parent>.section_main>.playlist{

}

.parent>.section_main>.playlist>.playlist_span{



    width: 60%;

}

.parent>.section_main>.playlist>.playlist_span>button{



}

.overflow{


}

@media only screen and (min-width: 1200px){

    .parent{

}

.parent>.section_main{

    grid-template-columns: 1fr 1fr;

}

.parent>.section_main>.main_article{






}

.parent>.section_main>.main_article>.main_span{








}

.parent>.section_main>.main_article>.main_span>.pick_song{



}
.parent>.section_main>.main_article>.main_span>.pick_song>p{



}

.parent>.section_main>.main_article>.main_span>.selection_span{

}

.parent>.section_main>.main_article>.main_span>.selection_span>span{




}

.selection_span>span>h3{


}
.selection_span>span>img{


}

.parent>.section_main>.main_article>.main_span>.buttons_span{


}  

.parent>.section_main>.main_article>.main_span>.buttons_span>button{



}
.parent>.section_main>.playlist{

}

.parent>.section_main>.playlist>.playlist_span{




}

.parent>.section_main>.playlist>.playlist_span>button{



}

.overflow{


}
}
    
}
</style>