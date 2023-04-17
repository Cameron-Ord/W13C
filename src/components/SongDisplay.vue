<template>
    <div>
        <article>

            <span>

                <button @click="show_post">PLAY MUSIC</button>


            

      
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

            show_post(post) {

                this.chosen_song= post;
            },

        },

        mounted:(){
            this.$root.$on(`highlight_post`, this.show_post)
        }

    }
</script>

<style scoped>

</style>