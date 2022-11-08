<script>
  $: currentnumber = 0;
  $: previousoperation = "";
  let previousnumber = "";
  let operator = "";

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

  function createOperation(newoperator) {
    if (newoperator == "÷") {
      newoperator = "/";
    }
    operator = newoperator;
    previousoperation = currentnumber + " " + operator;
    previousnumber = currentnumber;
    currentnumber = 0;
  }

  function equalsButton() {
    if (operator == "+") {
      previousoperation = "";
      currentnumber = Number(previousnumber) + Number(currentnumber);
    }
    if (operator == "-") {
      previousoperation = "";
      currentnumber = Number(previousnumber) - Number(currentnumber);
    }
    if (operator == "*") {
      previousoperation = "";
      currentnumber = Number(previousnumber) * Number(currentnumber);
    }
    if (operator == "/") {
      previousoperation = "";
      currentnumber = Number(previousnumber) / Number(currentnumber);
    }
    if (currentnumber == infinity){
      currentnumber = Calculation outside of expected range
    }
  }
</script>

<div id="output">
  <p id="previousoperation">{previousoperation}</p>
  <p id="currentnumber">{currentnumber}</p>
</div>
<div id="grid">
  <button class="operation" on:click={() => (currentnumber = 0)}>CE</button>
  <button
    class="operation"
    on:click={() => (currentnumber = 0)}
    on:click={() => (previousoperation = "")}
    on:click={() => (previousnumber = "")}
    on:click={() => (operator = "")}>C</button
  >

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
  <button class="operation" on:click={() => equalsButton()}>=</button>
</div>
