<script>
  import Message from "./Message.svelte";
  export let name;
  let messages = [];

  function addMessage(event) {
    console.log(event.detail);
    messages = [event.detail,...messages];
  }
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>{name}</h1>

<Message author="Ben" on:message={addMessage} />

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div>By {message.author}</div>
    <div>{message.text}</div>
    <hr />
  {/each}
</div>
