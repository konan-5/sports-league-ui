<template>
    <footer>
        <div class="container footer">
            <p>API Version: {{ version }}</p>
        </div>
    </footer>
</template>
<script>
export default {
    data() {
        return {
            version: '',
        }
    },
    mounted() {
        fetch('http://localhost:3001/api/version') // Replace with your API endpoint
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                return response.json();
            })
            .then(data => {
                this.version = data.version; // Update the items array with the received data
            })
            .catch(error => {
                console.error('Error fetching data:', error);
            });
    }
}
</script>

<style>
footer {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    z-index: 99;
}
.footer {
    background-color: #F6F7F7;
    display: flex;
    justify-content: end;
    align-items: center;
    height: 60px;
    

}

.footer p {
    font-size: 16px;
    font-family: 'Open Sans', sans-serif;
}
</style>