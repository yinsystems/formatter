<template>
    <main>
        <h4>Format Cards To Excel</h4>
        <textarea v-model="cardsData" rows="40" cols="130"></textarea>
        <button @click="formatCards" style="margin-bottom: 20px">Format Cards</button>
        <div v-if="response">
            <h4>Response from Server:</h4>
            <pre>{{ response }}</pre>
        </div>
    </main>
</template>

<script>
import axios from 'axios';

export default {

    data() {
        return {
            cardsData: "", // Data entered in the textarea
            response: null // Response from the server
        };
    },
    methods: {
        formatCards() {
            // Make a POST request to your API endpoint
            // Replace 'your-api-endpoint' with the actual API endpoint
            axios.post('https://waec.webbotics.cloud/format', {response: this.cardsData})
                .then(response => {
                    // Update the response in the component's state
                    this.response = response.data;
                })
                .catch(error => {
                    console.error('Error:', error);
                });
        }
    }
};
</script>

<style scoped>
/* Add your custom styles here */
</style>
