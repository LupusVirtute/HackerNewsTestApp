<script lang="ts">
	import type IStory from '../interfaces/IStory';
	import Story from './Story.svelte';
	export let stories: IStory[];
	let visible = true;
</script>
<stackLayout orientation="vertical">
	{#each stories as story}
		{#if visible}
			<Story {story} />
		{/if}
	{/each}
</stackLayout>
