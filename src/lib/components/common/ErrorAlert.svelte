<!-- src/lib/components/common/ErrorAlert.svelte -->
<script>
  export let message = '';
</script>

<div class="error-alert" role="alert" aria-live="assertive">
  <p>{message}</p>
</div>

<style>
  .error-alert {
    padding: 1rem;
    background-color: #f8d7da;
    color: #721c24;
    border: 1px solid #f5c6cb;
    margin-top: 1rem;
    border-radius: 4px;
  }
</style>
