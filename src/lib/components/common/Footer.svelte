<!-- src/lib/components/common/Footer.svelte -->
<footer>
  <p>&copy; 2024 College Evaluation System</p>
</footer>

<style>
  footer {
    text-align: center;
    padding: 1rem;
    background-color: #f1f1f1;
    position: fixed;
    width: 100%;
    bottom: 0;
    left: 0;
    border-top: 1px solid #ccc;
  }

  @media (max-width: 600px) {
    footer {
      padding: 0.5rem;
      font-size: 0.9rem;
    }
  }
</style>
