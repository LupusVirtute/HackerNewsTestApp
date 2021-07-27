<page>
    <actionBar title="Hacker News 👨‍💻" />
    <scrollView orientation="vertical" class="scroller">
		<DisplayNews {stories}/>
	</scrollView>
</page>

<script lang="typescript">
import {navigatingTo, animate} from './functions/animation';
import DisplayNews from './components/DisplayNews.svelte';
import IStory from './interfaces/IStory';

	let stories: IStory[] = [];
	async function getLatestStories(){
		let entryPoint = 'https://hacker-news.firebaseio.com/v0/';
		let topStories = entryPoint + "topstories.json";
		let storiesIDs = await getRequest(topStories);
		storiesIDs = storiesIDs.slice(0,100);
		let storyEntryPoint = entryPoint + 'item/';
		for(let item of storiesIDs){
			let endpoint = storyEntryPoint+item+'.json';
			let story = await getRequest(endpoint);
			stories = [...stories,story];
		}
	}
	async function getRequest(url){
		return await (await fetch(url)).json()
	}
	getLatestStories();

</script>

<style lang="sass">
page
	font-size: calc(15vw + 12px)
	background: #111
	color: #fff
actionbar
	background: #222
	color: #fff

</style>
