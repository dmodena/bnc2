<script>
    import { onMount } from 'svelte';
    import GameHeader from './game/GameHeader.svelte';
    import History from './game/History.svelte';
    import GuessView from './game/GuessView.svelte';
    import Status from './game/Status.svelte';
    import StartGameButton from './game/StartGameButton.svelte';
    import GiveUpButton from './game/GiveUpButton.svelte';
    import Keypad from './game/Keypad.svelte';

    let guess = [];
    let lastGuess = '';
    let guessAttempt = 0;
    let statusMessage = '';
    let history;
    let worker;

    onMount(() => {
        worker = new Worker('js/worker.js');
        worker.onmessage = receiveFromWorker;
    });

    function startGame() {
        worker.postMessage({ fn: 'startGame' });
    }

    function giveUp() {
        worker.postMessage({ fn: 'giveUp' });
    }

    function handleNumberPressed(e) {
        if (guess.length > 3)
            return;

        guess.push(e.detail);
        guess = [...guess];
    }

    function handleBackspace() {
        if (guess.length == 0)
            return;

        guess.pop();
        guess = [...guess];
    }

    function handleSubmit() {
        if (guess.length != 4)
            return;

        worker.postMessage({ fn: 'guess', val: guess });
        lastGuess = guess.join('');
        guessAttempt++;
        guess = [];
    }

    function handleHistory(e) {
        history.receiveHistory(guessAttempt, lastGuess, e);
    }

    function updateStatus(message) {
        statusMessage = message;
    }

    function receiveFromWorker(message) {
        switch (message.data.fn) {
            case 'startGame':
                updateStatus(message.data.val);
                break;
            case 'giveUp':
                updateStatus(message.data.val);
                break;
            case 'guess':
                console.log(message.data.val);
                handleHistory(message.data.val);
                break;
            default:
                break;
        }
    }
</script>

<div class="container">
    <GameHeader />
    <History bind:this={history} />
    <GuessView {guess} />
    <Status message={statusMessage} />
    <div class="row mt-3">
        <StartGameButton on:click={startGame} />
        <GiveUpButton on:click={giveUp}/>
    </div>
    <hr />
    <Keypad
        on:numberPressed={handleNumberPressed}
        on:submitPressed={handleSubmit}
        on:backspacePressed={handleBackspace} />
</div>
