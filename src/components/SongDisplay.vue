<template>
    <div>
        <article>

            <span>

                <button @click="play">PLAY MUSIC</button>

                <h1>{{ Object[`title`] }}</h1>


      
            </span>

        </article>
    </div>
</template>

<script>
    export default {
        
        props: {

            post: Object



        },


        methods:{


            play(){
                
                this.$emit(`highlight_post`, this.post);

            }
        }


    }
</script>

<style scoped>

</style>