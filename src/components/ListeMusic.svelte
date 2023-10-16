<script>
    import {supabase} from "../supabase"

    let promise = supabase.from("musics").select("url")
</script>

<h1>Voici les musiques</h1>
<div>
    {#await promise}
        <p>Loading ..</p>
    {:then {data, error}} 
        {#each data as musics}
            <a href={musics.url}>{musics.url}</a><br>
        {/each}
    {/await}
</div>

