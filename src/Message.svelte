<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let message = "";
  export let author;

  function saveMessage() {
    const newMessage = {
      id: Date.now(),
      text: message,
      author: author
    };
    console.log("newmessage", newMessage);
    dispatch("message", newMessage);
    message = "";
  }
</script>

<style>

</style>

<textarea cols="50" rows="5" bind:value={message} />
<br />
<button on:click={saveMessage}>Send</button>
