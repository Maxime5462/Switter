<script>
  export let name;
  let message = "";

  function updateMessage(event) {
    console.log(event.target.value);
    message = event.target.value;
  }
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>{name}</h1>
<textarea cols="50" rows="5" on:input={updateMessage} />
<div>
<h3>Preview</h3>
{message}
</div>
