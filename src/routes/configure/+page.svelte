<script lang="ts">
    import Keymap_display from "../../lib/Keymap_display.svelte";

    import Basic from "../../lib/Basic.svelte";
    import Media from "../../lib/Media.svelte";
    import Macros from "../../lib/Macros.svelte";
    import Layers from "../../lib/Layers.svelte";
    import Special from "../../lib/Special.svelte";
    import Lighting from "../../lib/Lighting.svelte";
    import Other from "../../lib/Other.svelte";

    let keymapTypeSwitch = 0;
    let menuSwitch = 0;
</script>

<header class="background-1 border-bottom">
    <nav>
        <div class="nav-link" style="margin-left: 0">
            <a href="/configure" class="text-active-bar">CONFIGURE</a>
        </div>
        <div class="nav-link">
            <a href="/key-tester" class="text-inactive-bar">KEY TESTER</a>
        </div>
        <div class="nav-link">
            <a href="/settings" class="text-inactive-bar">SETTINGS</a>
        </div>
    </nav>
</header>
<main>
    <div class="grid-item border-top border-right border-bottom">
        <div class="menu background-4">
            <div class="menu-list">
                <button class:active={menuSwitch === 0} class="text clickable" on:click={() => menuSwitch = 0}>
                    Keymap
                </button>
                <button class:active={menuSwitch === 1} class="text clickable" on:click={() => menuSwitch = 1}>
                    Macros
                </button>
                <button class:active={menuSwitch === 2} class="text clickable" on:click={() => menuSwitch = 2}>
                    Save/Load
                </button>
                <button class:active={menuSwitch === 3} class="text clickable" on:click={() => menuSwitch = 3}>
                    Lighting
                </button>
            </div>
        </div>
    </div>
    <div class="grid-item border-top border-left border-bottom background-2" style="position: relative">
        {#if menuSwitch === 0}
            <Keymap_display/>
        {/if}
        {#if menuSwitch === 1}{menuSwitch}{/if}
        {#if menuSwitch === 2}{menuSwitch}{/if}
        {#if menuSwitch === 3}{menuSwitch}{/if}
    </div>
    <div class="grid-item border-top border-right background-3">
        {#if menuSwitch === 0}
            <div class="menu">
                <div class="menu-list">
                    <button class="text clickable" class:active={keymapTypeSwitch === 0} on:click={() => keymapTypeSwitch = 0}>
                        Basic
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 1} on:click={() => keymapTypeSwitch = 1}>
                        Media
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 2} on:click={() => keymapTypeSwitch = 2}>
                        Macros
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 3} on:click={() => keymapTypeSwitch = 3}>
                        Layers
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 4} on:click={() => keymapTypeSwitch = 4}>
                        Special
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 5} on:click={() => keymapTypeSwitch = 5}>
                        Lighting
                    </button>
                    <button class="text clickable" class:active={keymapTypeSwitch === 6} on:click={() => keymapTypeSwitch = 6}>
                        Other
                    </button>
                </div>
            </div>
        {/if}
    </div>
    <div class="grid-item border-top border-left background-3">
        {#if keymapTypeSwitch === 0}<Basic/>{/if}
        {#if keymapTypeSwitch === 1}<Media/>{/if}
        {#if keymapTypeSwitch === 2}<Macros/>{/if}
        {#if keymapTypeSwitch === 3}<Layers/>{/if}
        {#if keymapTypeSwitch === 4}<Special/>{/if}
        {#if keymapTypeSwitch === 5}<Lighting/>{/if}
        {#if keymapTypeSwitch === 6}<Other/>{/if}
    </div>
</main>

<style lang="scss">
  header {
    width: 100%;
    height: 70px;
  }

  nav {
    width: 90%;
    max-width: 700px;
    height: 70px;
    margin: 0 auto;
    text-align: justify;
    &:after {
      content: '';
      display: inline-block;
      width: 100%;
    }
  }

  .nav-link {
    display: inline-flex;
    margin: 17.5px -2px;
    font-size: 30px;
    height: 35px;
  }

  a {
    text-decoration: none;
    white-space: nowrap;
  }

  main {
    height: calc(100vh - 71px);
    width: 100%;
    display: grid;
    grid-template-columns: 230px auto;
    grid-template-rows: calc(0.55 * calc(100vh - 71px)) calc(0.45 * calc(100vh - 71px));
  }
</style>