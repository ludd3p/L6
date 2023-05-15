<script>
    import {createEventDispatcher} from "svelte";
    export let show = false;
    export let text ="";

    const dispatch = createEventDispatcher();

    function closeModal() {
        show = false;
        dispatch("close");
    }
</script>
{#if show}
  <div class="popup">
    <div class="content">
      <div class="header">
        <button class="close-button" on:click={closeModal}>X</button>
      </div>
      <div class="body">
        <h2>{text}</h2>
      </div>
    </div>
  </div>
{/if}


<style>
    .popup {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 400px;
      background-color: white;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
      border-radius: 4px;
      z-index: 9999;
    }
  
    .content {
      padding: 20px;
    }
  
    .header {
      display: flex;
      justify-content: flex-end;
    }
  
    .close-button {
      padding: 4px 8px;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
