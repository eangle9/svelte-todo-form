<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
  export let tabs;
  export let activeTab;
</script>

<div class="tabs">
  <ul>
    {#each tabs as tab}
      <li on:click={() => dispatch('todo', tab)}>
        <div class="tab" class:active={activeTab === tab}>{tab}</div>
      </li>
    {/each}
  </ul>
</div>

<style>
    .tabs{
      margin: 20px auto;
      display: flex;
      justify-content: center;
    }
    ul{
        display: flex;
        list-style: none;
        gap: 50px;
        color: #555;
    }
    li{
        font-size: 18px;
        cursor: pointer;
    }
    .active{
        padding-bottom: 8px;
        color:blueviolet;
        border-bottom: 2px solid blueviolet;
    }

</style>
