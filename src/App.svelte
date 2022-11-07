<script>
  $: currentnumber = 0;
  $: previousoperation = "";

  function addNumber() {
    if (currentnumber.length == "16") {
      return;
    }
    if (currentnumber == 0) {
      currentnumber = "";
    }
    currentnumber = currentnumber + event.target.innerHTML;
  }

  function delnumber() {
    if (currentnumber !== 0) {
      currentnumber = currentnumber.slice(0, -1);
    }
    if (currentnumber == "") {
      currentnumber = 0;
    }
  }

  function createOperation(operation) {
    previousoperation = currentnumber + " " + operation;
    currentnumber = 0;
  }
</script>

<div id="output">
  <p id="previousoperation">{previousoperation}</p>
  <p id="currentnumber">{currentnumber}</p>
</div>
<div id="grid">
  <button
    class="operation"
    on:click={() => (currentnumber = 0)}
    on:click={() => (previousoperation = "")}>CE</button
  >
  <button class="operation" on:click={() => (currentnumber = 0)}>C</button>

  <button class="operation" on:click={() => delnumber()}>DEL</button>

  <button class="operation" on:click={() => createOperation("/")}>÷</button>
  <button class="number" on:click={() => addNumber(event)}>1</button>
  <button class="number" on:click={() => addNumber(event)}>2</button>
  <button class="number" on:click={() => addNumber(event)}>3</button>
  <button class="operation" on:click={() => createOperation("*")}>*</button>
  <button class="number" on:click={() => addNumber(event)}>4</button>
  <button class="number" on:click={() => addNumber(event)}>5</button>
  <button class="number" on:click={() => addNumber(event)}>6</button>
  <button class="operation" on:click={() => createOperation("+")}>+</button>
  <button class="number" on:click={() => addNumber(event)}>7</button>
  <button class="number" on:click={() => addNumber(event)}>8</button>
  <button class="number" on:click={() => addNumber(event)}>9</button>
  <button class="operation" on:click={() => createOperation("-")}>-</button>
  <button class="number" on:click={() => addNumber(event)}>⁺∕₋</button>
  <button class="number" on:click={() => addNumber(event)}>.</button>
  <button class="number" on:click={() => addNumber(event)}>0</button>
  <button class="operation">=</button>
</div>
