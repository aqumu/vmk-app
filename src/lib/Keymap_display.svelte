<script lang="ts">
    export let layerSwitch = 0;
    interface BoardList {
        boards: string[];
        selectedBoard: number;
        isOpen: boolean;
    }
    export let boardList: BoardList = {
        boards: ['VM35', 'BKS65', 'VM67'],
        selectedBoard: 0,
        isOpen: false,
    }

    let n = 0;
    let unusedBoards:string[] = [];

    for (let i = 0; i < boardList.boards.length; i++) {
        if (i != boardList.selectedBoard) {
            unusedBoards[n] = boardList.boards[i]
            n++
        }
    }
</script>

<svg xmlns="http://www.w3.org/2000/svg" style="display: none;" >
    <symbol id="caret" viewBox="0 0 320 512">
        <path d="M137.4 374.6c12.5 12.5 32.8 12.5 45.3 0l128-128c9.2-9.2 11.9-22.9 6.9-34.9s-16.6-19.8-29.6-19.8L32 192c-12.9 0-24.6 7.8-29.6 19.8s-2.2 25.7 6.9 34.9l128 128z"/>
    </symbol>
</svg>

<div class="layer">
    <div class="layer-item text" style="color: #FFFFFF; cursor: default;">L</div>
    <button on:click={() => layerSwitch = 0} class:active-alt={layerSwitch === 0} class="layer-item text-alt clickable">0</button>
    <button on:click={() => layerSwitch = 1} class:active-alt={layerSwitch === 1} class="layer-item text-alt clickable">1</button>
    <button on:click={() => layerSwitch = 2} class:active-alt={layerSwitch === 2} class="layer-item text-alt clickable">2</button>
    <button on:click={() => layerSwitch = 3} class:active-alt={layerSwitch === 3} class="layer-item text-alt clickable">3</button>
</div>
<button class:unclipped={boardList.isOpen} style="clip-path: inset(0px 0px {44 * unusedBoards.length + 7}px 0px round 10px);" class="boards" on:click={() => boardList.isOpen = !boardList.isOpen}>
    {boardList.boards[boardList.selectedBoard]}
    <svg class:rotated={boardList.isOpen} width="24" height="24" style="transition: rotate 0.3s;"><use xlink:href="#caret"/></svg>
    {#each boardList.boards as board, i}
        {#if boardList.selectedBoard !== i}
            <button on:click={() => boardList.selectedBoard = i} class="boards-nonselected">
                {board}
            </button>
        {/if}
    {/each}
</button>

<style lang="scss">
  .layer {
    position: absolute;
    top: 20px;
    left: 25px;
    display: flex;
  }

  .layer-item {
    font-size:  33px;
    padding-right: 23px;
    line-height: 49px;
  }

  .boards {
    font-family: "Raleway", sans-serif;
    font-weight: 600;
    font-size: 33px;
    color: #FFFFFF;
    transition: all 0.3s ease;
    display: inline;
    padding: 7px;
    position: absolute;
    top: 20px;
    right: 25px;
  }

  .unclipped {
    clip-path: inset(0% 0% 0% 0% round 10px) !important;
    background-color: #181818;
  }

  .boards-nonselected {
    padding-top: 5px;
    display: block;
  }

  #caret {
    fill: #FFFFFF;
    rotate: 0deg;
  }

  .rotated {
    rotate: 180deg;
    transition: rotate 0.5s;
  }
</style>