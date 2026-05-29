<script>
  import TransactionItem from '$lib/components/TransactionItem.svelte';
  
  const transactions = [
    { id: 1, title: 'Lohn', date: '2026-05-01', amount: 1400.00, type: 'income' },
    { id: 2, title: 'Shell-Tankstelle', date: '2026-05-03', amount: -94.00, type: 'expense' },
    { id: 3, title: 'McDonalds', date: '2026-05-05', amount: -4.39, type: 'expense' },
    { id: 4, title: 'REWE Supermarkt', date: '2026-05-06', amount: -52.18, type: 'expense' }
  ];

  

</script>  

<section class="transactions-section">
  <h2 class="section-title">Transaktionen</h2>

  <div class="list-container">
    {#each transactions as tx (tx.id)}
      <TransactionItem {tx} />
    {/each}
  </div>
</section>

<style>
  .section-title {
    font-size: 1.3rem;
    font-weight: 600;
    margin-bottom: 15px;
  }

  .list-container {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
</style>