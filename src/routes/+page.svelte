<script>
	import { page } from '$app/stores';
	import { superForm } from 'sveltekit-superforms/client';
	export let data;
	const { form, errors, constraints, message } = superForm(data.form);
</script>

<svelte:head>
	<title>LNBCK is coming soon</title>
	<meta name="description" content="Sign up for a new kind of news program." />
</svelte:head>

<h1 class="text-2xl">LeaNaBaCK</h1>

<div class="my-4">
	<p class="mb-4">Sign up for a new kind of news program.</p>
</div>


<div class="my-4 bg-violet-200 p-2 rounded-lg">
	<h2 class="text-xl mb-1">Receive an Invite when we launch</h2>

	<form method="POST">
		<div class="mb-2">
			<input
				class="border px-2 py-1 rounded min-w-[300px]"
				type="email"
				name="email"
				bind:value={$form.email}
				placeholder="your@email.com"
				data-invalid={$errors.email}
				{...$constraints.email}
			/>
			{#if $errors.email}<span class="bg-red-700">{$errors.email}</span>{/if}
		</div>

		<div>
			<button class="bg-violet-800 text-white hover:bg-violet-950 px-4 py-1 rounded">Signup</button>
		</div>
	</form>

	{#if $message}
		<div class="bg-white mt-2 p-2 rounded {$page.status === 200 ? 'text-green-800': 'text-red-800'}">{$message}</div>
	{/if}
</div>
