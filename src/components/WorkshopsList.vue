<template>
    <div>
        <h1>List of Workshops!</h1>
        <hr />
        <ol>
            <li v-for="workshop in workshops" :key="workshop._id">
                <h2>{{workshop.name}}</h2>
                <div>Speaker: {{workshop.speaker}}</div>
            </li>
        </ol>
    </div>
</template>

<script>
    import axios from 'axios';
    
    export default {
        name: 'WorkshopsList',
        data() {
            return {
                workshops: []
            };
        },
        created() {
            axios.get( `${process.env.VUE_APP_API_BASE_URL}/workshops` )
                .then(response => {
                    this.workshops = response.data;
                    console.log( this.workshops );
                })
                .catch(error => {
                    alert( error.message )
                });
        }
    };
</script>

<style scoped>
</style>