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
    <div>
        {#each teams as team}
            <div style="color:{team.primary};">
                {team.city} {team.nickname}
            </div>
        {/each}
    </div>
</div>

<style>

</style>