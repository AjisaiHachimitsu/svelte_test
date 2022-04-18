<script lang="ts">
	//export let name: string;
	import TodoInputForm from './ToDoInputForm.svelte';
  import ToDoList from './ToDoList.svelte';
	let firstName="";
	let lastName="";
	let nameEntered=false;
	$:fullName=firstName+'　'+lastName;
  function handleSubmit()
  {
    if(lastName&&firstName) nameEntered=true;
  }
</script>

<main>
	<!-- <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->
	{#if nameEntered}
	<h1>タスクリストアプリケーションへようこそ、{fullName}さん!</h1>
	<TodoInputForm userName={fullName} />
  <ToDoList />
	{:else}
	<h1>タスクリストアプリケーションへようこそ!</h1>
  <h3>名前を入力してください。</h3>
  <form on:submit|preventDefault={handleSubmit} >
  <div>
    <input bind:value={lastName} type="text" placeholder="姓" required>
  </div>
  <div>
    <input bind:value={firstName} type="text" placeholder="名" required>
  </div>
  <button type="submit">タスク管理を始める</button>
  </form>
  {/if}
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