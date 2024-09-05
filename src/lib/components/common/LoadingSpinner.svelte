<!-- src/lib/components/common/LoadingSpinner.svelte -->
<div class="spinner" aria-label="Loading"></div>

<style>
  .spinner {
    border: 4px solid rgba(0, 0, 0, 0.1);
    width: 36px;
    height: 36px;
    border-radius: 50%;
    border-left-color: #09f;
    animation: spin 1s linear infinite;
    display: inline-block;
  }

  @keyframes spin {
    to {
      transform: rotate(360deg);
    }
  }
</style>
