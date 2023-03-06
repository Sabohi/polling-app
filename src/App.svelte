<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import PollList from "./components/PollList.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import Tabs from "./shared/Tabs.svelte";

	// Tabs
	let items = ['Current Polls', 'Add New Tab'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}

	// // Polls
	// let polls = [
	// 	{
	// 		id: 1,
	// 		question: 'Python or JavaScript?',
	// 		answerA: 'Python',
	// 		answerB: 'JavaScript',
	// 		votesA: 9,
	// 		votesB: 15,
	// 	},
	// ];

	const handleAdd = () => {
		// const poll = e.detail;
		// polls = [poll, ...polls];
		// console.log(polls);
		activeItem = 'Current Polls';
	}

	// const handleVote = (e) => {
	// 	const { id, option } = e.detail;
	// 	let pollsCopy = [...polls];
	// 	let upvotedPolls = 	pollsCopy.find((poll) => poll.id === id);
	// 	upvotedPolls[option]++;

	// 	polls = pollsCopy;
	// }
</script>

<Header />

<main>
	<Tabs 
		{items}
		{activeItem}
		on:tabChange={tabChange}
	/>
	{#if activeItem === 'Current Polls'}
		<PollList />
	{:else if activeItem === 'Add New Tab'}
		<CreatePollForm on:add={handleAdd} />
	{/if}
</main>

<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>