<script>
  import Message from "./Message.svelte";
  export let name;
  let messages = [];
  let isVisible = true;

  function addMessage(event) {
    console.log(event.detail);
    messages = [event.detail, ...messages];
  }

  const options = {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
    hour24: true,
    hour: "numeric",
    minute: "2-digit",
    second: "2-digit"
  };

  const formatter = new Intl.DateTimeFormat("fr-FR", options);

  function toggle() {
    isVisible = !isVisible;
  }
</script>

<style>
  h1 {
    color: purple;
  }
  .author {
    font-weight: bold;
  }
</style>

<h1>{name}</h1>
<button on:click={toggle}>{isVisible ? 'hide' : 'show'}</button>
<br />
{#if isVisible}
  <Message on:message={addMessage} />
{/if}

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div class="author">
      Par {message.author} , le {formatter.format(message.date)}
    </div>
    <div>{message.text}</div>
    <hr />
  {/each}
</div>
