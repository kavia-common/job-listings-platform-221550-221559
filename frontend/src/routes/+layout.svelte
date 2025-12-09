<script lang="ts">
    import '../app.css';
    let { children } = $props();
</script>

<header class="ocean-header">
    <div class="container inner">
        <div class="app-title" aria-label="Job Board">
            <span class="dot" aria-hidden="true"></span>
            <span>Ocean Jobs</span>
        </div>
        <nav aria-label="Top Navigation">
            <a href="/" class="text-muted">Home</a>
        </nav>
    </div>
</header>

<main>
    <div class="container" style="padding-top: 1.25rem; padding-bottom: 2rem;">
        {@render children()}
    </div>
</main>
