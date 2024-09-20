<script lang="ts">
    import { Listgroup } from 'svelte-5-ui-lib'
    import { Listgroup as ListgroupWithFix } from '$lib'

    let items = $state([{
        name: 'Item without onclick'
    }, {
        name: 'Item with onclick',
        onclick: () => { alert('Clicked Item')}
    }])
</script>

<div class="example">
    <h1>Example #1: without onclick on Listgroup</h1>
    <h2>Using existing Listgroup</h2>
    <Listgroup active {items}>test</Listgroup>
    Expected that the second item could be clicked and showed the item specific alert message. Instead nothing
    happened at all.

    <h2>Using Listgroup with minor fix</h2>
    <ListgroupWithFix active {items}/>

</div>
<div class="example">
    <h1>Example #2: with onclick on Listgroup</h1>
    <h2>Using existing Listgroup</h2>
    <Listgroup active {items} onclick={() => alert('Clicked group')}/>
    Expected that clicking the first item would show the generic group alert message, but the second item, when
    clicked, showed the item specific alert message. Instead both items showed the generic group alert message.

    <h2>Using Listgroup with minor fix</h2>
    <ListgroupWithFix active {items} onclick={() => alert('Clicked group')}/>
</div>

<style>
    .example {
        @apply flex flex-col max-w-96 p-4 dark:text-gray-50 gap-2 text-sm mb-8;
    }
    h1 {
        @apply text-lg border-b;
    }
    h2 {
        @apply text-base italic mt-2 border-b border-dashed;
    }
</style>