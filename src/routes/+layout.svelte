<script>
    import "../app.pcss";
    let { children } = $props();
</script>

<div id="content" class="w-full h-full min-h-screen bg-primary-50 dark:bg-gray-900">
    <main class="min-w-0 max-w-full flex-auto lg:static lg:overflow-visible max-h-full h-full">
        <div id="mainContent">
            {@render children()}
        </div>
    </main>
</div>