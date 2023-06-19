<script>
  export let type = "primary";
  export let inverse = false;
</script>

<button class={type} class:reverse={inverse}>
  <slot></slot>
</button>

<style>
  button {
    margin-top: 10px;
    padding: 8px 12px;
    border-radius: 6px;
    cursor: pointer;
  }
  .primary {
    background-color: darkturquoise;
    color: #fff;
  }
  .primary:focus{
    background-color: rgb(15, 85, 85);
    color: #fff;
  }
  .primary:hover{
    background-color: darkcyan;
  }
  .secondary{
    background-color: dodgerblue;
    color: #fff;
  }
  .error{
    background-color: red;
    color: #fff;
  }
  .primary.reverse{
    background-color: #fff;
    color: darkturquoise;
    border: 1px solid darkturquoise;
  }
  .secondary.reverse{
    background-color: #fff;
    color: dodgerblue;
    border: 1px solid dodgerblue;
  }
  .error.reverse{
    background-color: #fff;
    color: red;
    border: 1px solid red;
  }
</style>
