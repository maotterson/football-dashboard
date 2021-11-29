<script>
	import { onMount } from 'svelte';

	let teams = [];

	onMount(async () => {
		// @ts-ignore
		const res = await fetch(import.meta.env['VITE_TEAMS_API_URL']);
		teams = await res.json();
	});

    
</script>

<div class="teams">
    {#each teams as team}
        <div class="team" style="background-color:{team.primary};">
            {team.city} {team.nickname}
        </div>
    {/each}
</div>

<style>
.teams{
    display:flex;
    flex-direction: column;
}
.team{
    padding:10px;
    border:1px rgb(213, 213, 213) solid;
    border-radius:999px;
    width:max-content;
    margin-bottom:5px;
    margin-right:5px;
    font-family:sans-serif;
    font-weight:bold;
    color:white;
}
</style>