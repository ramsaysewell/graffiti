<script lang="ts">
  import { slide } from "svelte/transition";
  import type { ThemeValues } from "./types";

  let { theme_values = $bindable() }: { theme_values: ThemeValues } = $props();

  let theming = $state(true);
</script>

<div class="theme-controls">
  <button onclick={() => (theming = !theming)}>Theme This Page ⇣</button>

  {#if theming}
    <div transition:slide class="cluster">
      {#each Object.keys(theme_values) as key}
        <label>
          {key.replace("_", "-")}:
          <input type="color" bind:value={theme_values[key]} />
        </label>
      {/each}
    </div>
  {/if}
</div>

<style>
  .theme-controls {
    position: sticky;
    top: 0;
    background: var(--bg);
  }

  .cluster {
    padding: var(--pad-m) var(--vs-l);
    align-items: center;
    border-bottom: var(--border-1);
    input {
      margin-bottom: 0;
    }
  }

  button {
    width: 100%;
    background: transparent;
  }
</style>
