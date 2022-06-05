<script>
	import Nested from './Nested.svelte'
	export let name;
	let age = 18
	let count = 0
	// 响应式声明
	$: doubled = count *2
	// 只要更改count 的值，我们就可以在控制台输出它的值
    $: console.log(`the count is ${count}`);
	$: {
		//console.log(`the count is ${count}`);
		alert(`I SAID THE COUNT IS ${count}`);
	}
	//你甚至可以将$:放在一个if语句之前：
	$: if (count >= 10) {
		alert(`count is dangerously high!`);
		count = 9;
	}

	function handleClick() {
		count += 1
	}

	let user = { loggedIn: false }
	function toggle() {
	    user.loggedIn = !user.loggedIn;
	  }

	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];

	import Thing from './Thing.svelte';

	  let things = [
	    { id: 1, color: 'darkblue' },
	    { id: 2, color: 'indigo' },
	    { id: 3, color: 'deeppink' },
	    { id: 4, color: 'salmon' },
	    { id: 5, color: 'gold' }
	  ];

	  function handleClick1() {
	    things = things.slice(1);
	  }


</script>

<main>
	<h1>Hello {name}! {age}</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click={handleClick}>
		Clicked {count} {count===1?'time':'times'}
	</button>
	<p>{count} doubled is {doubled}</p>
	<Nested answer={45} />
	<Nested  />
	<!-- <Info {...pkg}/> -->
	{#if user.loggedIn}
	  <button on:click={toggle}>Log out</button>
	{:else}
	  <button on:click={toggle}>Log in</button>
	{/if}

	{#each cats as cat}
		<li>
		<a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a>
		</li>
	{/each}

	<button on:click={handleClick1}>Remove first thing</button>

	{#each things as thing}
	  <Thing current={thing.color}/>
	{/each}

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>