<script>
	// export let name;
	let firstName = 'Rajan';
	let lastName = 'Sharma';
	let beltColor = 'black';

	// Reactive value 
	$: fullName = `${firstName} ${lastName}`;
	// $: console.log(beltColor);
	$: {
		console.log(beltColor);
		console.log(fullName);
	}
	const handleClick = () => {
		beltColor = 'orange';
	};

	const handleInput = (event) => {
		beltColor = event.target.value;
	};


	// Loops
	let people = [
		{name: 'yoshi',beltColor:'black',age:25,id:1},
		{name: 'mario',beltColor:'orange',age:45,id:2},
		{name: 'luigi',beltColor:'brown',age:35,id:3}
	];

	const handleNewBtn = (event,id) => {
		// delete the person from people
		// console.log(e.target.value);
		console.log(id);
		people = people.filter((per) => per.id != id);
		console.log(event);
		
	}

</script>

<main>
	<!-- <h1>Hello {name}!</h1> -->
	<!-- <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->

	<!-- <p style="color: {beltColor}">{beltColor} belt</p> -->

	<!-- <button on:click={handleClick}>update belt color</button> -->

	<!-- One way data binding -->
	<!-- <input type="text" on:input={handleInput} value = {beltColor}> -->

	<!-- <p>{beltColor} belt</p> -->
	<p>{fullName} {beltColor} belt</p>

	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>

	<!-- two way data binding -->
	<input type="text" bind:value={beltColor}>


	<!-- Loops -->
	<!-- <div>
		<h4>{people[0].name}</h4>
		<p>{people[0].beltColor}</p>
	</div> -->

	{#each people as person(person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.age} years old, {person.beltColor} belt</p>

			<!-- we use inline function -->
			<!-- <button on:click={handleNewBtn(person.id)}>Delete</button> -->

			<!-- inline function () => {} -->
			<button on:click={(event) => {
				// console.log('clicked me');
				handleNewBtn(event,person.id);
			}}>Delete</button>
		</div>

		{:else}
			<p>There are no people to show...</p>

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