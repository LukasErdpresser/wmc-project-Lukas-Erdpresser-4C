<script>
  let { tx } = $props();

  function formatAmount(amount, type) {
    const formatted = amount.toFixed(2) + '€';
    return type === 'income' ? `+${formatted}` : formatted;
  }
</script>

<article class="transaction-item">
  <div class="icon-circle {tx.type}">
    {#if tx.type === 'income'}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
        <line x1="7" y1="17" x2="17" y2="7"></line>
        <polyline points="7 7 17 7 17 17"></polyline>
      </svg>
    {:else}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
        <line x1="7" y1="7" x2="17" y2="17"></line>
        <polyline points="17 7 17 17 7 17"></polyline>
      </svg>
    {/if}
  </div>

  <div class="details">
    <span class="title">{tx.title}</span>
    <time class="date" datetime={tx.date}>{tx.date}</time>
  </div>

  <span class="amount {tx.type}">
    {formatAmount(tx.amount, tx.type)}
  </span>
</article>

<style>
  .transaction-item {
    background-color: #ffffff;
    border: 1px solid #eef0f2;
    border-radius: 12px;
    padding: 16px;
    display: flex;
    align-items: center;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.02);
  }

  .icon-circle {
    width: 42px;
    height: 42px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 16px;
    flex-shrink: 0;
  }

  .icon-circle.income {
    background-color: #e8f5e9;
    color: #2e7d32;
  }

  .icon-circle.expense {
    background-color: #ffebee;
    color: #c62828;
  }

  .icon-circle svg {
    width: 18px;
    height: 18px;
  }

  .details {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    gap: 4px;
  }

  .title {
    font-weight: 600;
    font-size: 1rem;
    color: #111;
  }

  .date {
    font-size: 0.85rem;
    color: #888;
  }

  .amount {
    font-weight: 600;
    font-size: 1.05rem;
  }

  .amount.income {
    color: #2e7d32;
  }

  .amount.expense {
    color: #c62828;
  }
</style>