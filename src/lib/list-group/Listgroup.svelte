<script lang="ts">
    import { setContext } from 'svelte';
    import { ListgroupItem } from 'svelte-5-ui-lib';
    import { type ListgroupProps as Props, listGroup } from 'svelte-5-ui-lib';

    let { children, items, active, onclick, rounded = true, border = true, class: className, ...restProps }: Props = $props();
    const base = $derived(listGroup({ rounded, border, className }));
    let tag = active ? 'div' : 'ul';
    setContext('active', active);
</script>

<svelte:element this={tag} {...restProps} class={base}>
    {#if items}
        {#each items as item}
            {#if typeof item === 'string'}
                <ListgroupItem {active} {onclick}>{item}</ListgroupItem>
            {:else}
                <!-- Below is the only line that is changed.
                     It now checks if an item 'onclick' is present and uses that if present. If not, it
                     uses the onclick of the parent 'Groupitem', which might be 'undefined' too. -->
                <ListgroupItem {active} {...item} onclick={item.onclick ? item.onclick : onclick}>{item}</ListgroupItem>
            {/if}
        {/each}
    {:else if children}
        {@render children()}
    {/if}
</svelte:element>

<!--
@component
[Go to docs](https://svelte-5-ui-lib.codewithshin.com/)
## Props
@prop children
@prop items
@prop active
@prop onclick
@prop rounded = true
@prop border = true
@prop class: className
@prop ...restProps
-->