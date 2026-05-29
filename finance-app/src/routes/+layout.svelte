<script>
	import favicon from '$lib/assets/favicon.svg';
	import { goto } from '$app/navigation';

	let { children } = $props();
	let number = $state('1.245,60 €');
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="container">
	<header class="account-header">
		<span class="label">Konto</span>
		<h1 class="balance">{number}</h1>
	</header>

	<nav class="tabs">
		<button onclick={() => goto('/')} class="tab">Transaktionen</button>
		<button onclick={() => goto('/statistic')} class="tab">Statistiken</button>
		<button onclick={() => goto('/chat')} class="tab">Chat-Beratung</button>
	</nav>

	{@render children()}
</main>

<style>
:global(body) {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    background-color: #f8f9fa;
    margin: 0;
    padding: 0;
    color: #333;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }

  .account-header {
    margin-bottom: 15px;
  }

  .account-header .label {
    font-size: 0.9rem;
    color: #666;
    display: block;
    margin-bottom: 4px;
  }

  .balance {
    font-size: 1.8rem;
    font-weight: 500;
    color: #2e7d32;
    margin: 0;
  }

  .tabs {
    display: flex;
    gap: 15px;
    border-bottom: 1px solid #e0e0e0;
    padding-bottom: 15px;
    margin-bottom: 25px;
  }

  .tab {
    background: none;
    border: none;
    padding: 8px 16px;
    font-size: 0.95rem;
    color: #666;
    cursor: pointer;
    border-radius: 20px;
    transition: all 0.2s ease;
  }

  .tab.active {
    background-color: #d8e5ff;
    color: #1a56db;
    font-weight: 500;
  }
</style>