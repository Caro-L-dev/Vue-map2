<template>
    <article>
        <h3>{{ adress.agency }}</h3>
        <p>{{ adress.infos }}</p>
    </article>
</template>

<script>
    
    export default {
        props: [ "adress" ]
    };
</script>
