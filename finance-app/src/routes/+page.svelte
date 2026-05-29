<script>

  const transactions = [
    { id: 1, title: 'Lohn', date: '2026-05-01', amount: 1400.00, type: 'income' },
    { id: 2, title: 'Shell-Tankstelle', date: '2026-05-03', amount: -94.00, type: 'expense' },
    { id: 3, title: 'McDonalds', date: '2026-05-05', amount: -4.39, type: 'expense' },
    { id: 4, title: 'REWE Supermarkt', date: '2026-05-06', amount: -52.18, type: 'expense' }
  ];

  function formatAmount(amount, type) {
    const formatted = amount.toFixed(2) + '€';
    return type === 'income' ? `+${formatted}` : formatted;
  }

  let number = 123;
</script>

<main class="container">
  <header class="account-header">
    <span class="label">Konto</span>
    <h1 class="balance">{number}</h1>
  </header>

  <nav class="tabs">
    <button class="tab active">Transaktionen</button>
    <button class="tab">Statistiken</button>
    <button class="tab">Chat-Beratung</button>
  </nav>

  <section class="transactions-section">
    <h2 class="section-title">Transaktionen</h2>

    <div class="list-container">
      {#each transactions as tx (tx.id)}
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
      {/each}
    </div>
  </section>
</main>

<style>
  /* Grund-Setup & Schriftart ähnlich dem Screenshot (Segoe UI / San Francisco) */
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

  /* Header */
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
    color: #2e7d32; /* Das typische Banking-Grün aus dem Screenshot */
    margin: 0;
  }

  /* Navigation Tabs */
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

  /* Transaktionsliste */
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

  /* Einzelne Transaktions-Zeile */
  .transaction-item {
    background-color: #ffffff;
    border: 1px solid #eef0f2;
    border-radius: 12px;
    padding: 16px;
    display: flex;
    align-items: center;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.02);
  }

  /* Icon Kreise */
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

  /* Details (Mitte) */
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

  /* Betrag (Rechts) */
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