<script>
    export let personagen;
</script>

<div class="personagem">
    <img src={personagen.image} alt={personagen.name} />
    <h1>{personagen.name}</h1>
    <h3>{personagen.species}</h3>
</div>