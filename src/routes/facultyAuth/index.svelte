<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      // Check if the user is authenticated (e.g., check authentication state or token)
      const isAuthenticated = true; // Example: Assume the user is authenticated for now
  
      // If the user is authenticated, redirect to the faculty dashboard
      if (isAuthenticated) {
        goto('/'); // Redirect to faculty dashboard (you might have a different route for faculty)
      }
    });
  </script>
  