<script lang="ts">
	import { fade } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import type IStory from '../interfaces/IStory';
	export let story: IStory;
	let visible = true;
	console.log("wowie a test!");
	window.setTimeout(()=> visible = !visible,300);
</script>
<style lang="sass">
.layout
	background: #333
	color: #fff
	padding: 15rem
	margin-bottom: 5rem
	margin-top: 5rem
	border-radius: 10rem
	width: 90%
	translate: all 1s
	.author
		color: #fff
		width: 100%
		border: 1px solid #600
</style>
{#if !visible}
<stackLayout class="layout" id="layoutStak{story.id}">
	<textField transition:fade  class="author" text="Author : {story.by}" editable="{false}"/>
	<label textWrap="true" text="{story.title}" editable="{false}"/>
</stackLayout>
{/if}
