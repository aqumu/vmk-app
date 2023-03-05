<script lang="ts">
    let selectedNow: string;
    function select(val) {
        selectedNow = val;
    }
</script>

<div class="menu">
    <button class="keycode" class:keycode-selected={selectedNow === "Enter"} on:click={() => select("Enter")}>Enter</button>
    <button class="keycode" class:keycode-selected={selectedNow === "Backspace"} on:click={() => select("Backspace")}>BckSp</button>
    <button class="keycode" class:keycode-selected={selectedNow === "Delete"} on:click={() => select("Delete")}>Del</button>
</div>