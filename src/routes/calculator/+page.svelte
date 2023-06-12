<style>
    * {
        color: white;
        font-family: "Outfit", Sans-serif;
        font-weight: 400px;
    }

    .wrapper {
        width: 100vw;
        height: 100vh;

        display: flex;
        justify-content: center;
        align-items: center;
    }

    .calculator {
        width: 340px;
        height: 400px;

        background-color: #252525;
        border-radius: 5px;

        display: flex;
        flex-direction: column;
        
        align-items: center;
    }

    .display {
        margin-top: 15px;

        width: 90%;
        height: 40px;

        border: white 1px solid;
        border-radius: 5px;

        display: flex;
        justify-content: center
    }

    .display input {
        background: none;
        border: none;

        width: 95%;
        font-size: 15px;

        letter-spacing: 2px;
    }

    .buttons {
        width: 90%;
        margin-top: 15px;

        height: 300px;
        display: flex;
        flex-wrap: wrap;

        gap: 10px;
        justify-content: center;
    }

    .button {
        width: calc((100% / 4) - 10px);
        height: calc((100% / 5) - 10px);

        background-color: #303030;
        border: none;
        font-size: 15px;
        border-radius: 5px;

        transition: background-color 0.3s ease;
    }
    .button:hover {
        background-color: #404040;
    }
    .button:active {
        transform: scale(0.95);
    }

</style>

<script>
    const buttons = [
        "(",
        ")",
        "%",
        "AC",
        "7",
        "8",
        "9",
        "/",
        "4",
        "5",
        "6",
        "*",
        "1",
        "2",
        "3",
        "-",
        "0",
        ".",
        "=",
        "+",
    ]

    const special = [
        "AC",
        "=",
    ]

    let display = undefined
    let equation = ""
    
    function addToEquation(event) {
        const button = event.target.innerText

        if (special.includes(button)) {

            if (button == "=") {
                equate()
                return
            }

            if (button == "AC") {
                equation = ""
                display.value = ""
                return
            }
        }

        equation += button
        display.value = equation
    }

    function equate() {
        try {
            display.value = eval(equation)
        } catch (error) {
            display.value = "Err"
            return
        }
    }
</script>

<div class='wrapper'>
    <div class='calculator'>
        <div class="display">
            <input bind:this={display}> 
        </div>

        <div class='buttons'>
            {#each buttons as button}
                <button class="button" on:click={addToEquation}>{button}</button>
            {/each}
        </div>
    </div>
</div>