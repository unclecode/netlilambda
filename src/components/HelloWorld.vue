<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <a href @click.prevent="call">call me</a>
    </div>
</template>

<script>
export default {
    name: "HelloWorld",
    data() {
        return {
            msg: "Welcome to Your Vue.js App"
        };
    },
    methods: {
        call() {
            fetch("/.netlify/functions/hello")
                .then(r => r.text())
                .then(d => {
                    this.msg = d;
                });
            //this.msg = "tes";
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
    font-weight: normal;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
