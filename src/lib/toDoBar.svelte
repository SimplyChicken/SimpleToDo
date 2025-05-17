<script>
    import { createEventDispatcher } from 'svelte';

    let value = '';
  
    function autoResize(event) {
      const textarea = event.target;
      textarea.style.height = 'auto';
      textarea.style.height = textarea.scrollHeight + 'px';
    }

    const dispatch = createEventDispatcher();
    function handleRemove() {
        dispatch('remove');
    }
  </script>
  
  <div style="display: flex; align-items: center; width: 27.1875vw;">
    <textarea
      bind:value
      placeholder="Enter New Task!"
      on:input={autoResize}
      class="resize-none overflow-hidden w-full p-2 border rounded"
      rows="1"
    />
    <button class="removeBtn" on:click={handleRemove}></button>
  </div>
  