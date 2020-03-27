<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let message = "";
  let author = "";
  let maxLength = 24;
  $: nbCaracters = message.length;
  $: disabled = message.length > maxLength ? true : false;

  function saveMessage() {
    const newMessage = {
      id: Date.now(),
      text: message,
      author: author || "anonymous",
      date: new Date()
    };
    dispatch("message", newMessage);
    message = "";
    author = "";
  }
</script>

<style>
  .text {
    width: 490px;
  }

  .alert {
    color: orangered;
  }
</style>

<input class="text" type="text" bind:value={author} />
<br />
<textarea cols="50" rows="5" bind:value={message} />
<br />
<button on:click={saveMessage} {disabled}>Send</button>
<span class:alert={nbCaracters > maxLength}>{nbCaracters}</span>
{#if disabled}
  <span class="alert">(message trop long)</span>
{/if}
