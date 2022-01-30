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
    let worker;

    onMount(() => {
        worker = new Worker('js/worker.js');
        worker.onmessage = receiveFromWorker;
    });

    function startGame() {
        console.log('Clicked start game');
        worker.postMessage({ fn: 'startGame' });
    }

    function giveUp() {
        console.log('Clicked give up');
        worker.postMessage({ fn: 'giveUp' });
    }

    function receiveFromWorker(message) {
        switch (message.data.fn) {
            case 'startGame':
                console.log('started game : )');
                break;
            case 'giveUp':
                console.log('gave up : (');
                break;
            case 'guess':
                console.log('you guessed sth : S');
                break;
            default:
                break;
        }
    }
</script>

<div class="container">
    <GameHeader />
    <History />
    <GuessView />
    <Status />
    <div class="row mt-3">
        <StartGameButton on:click={startGame} />
        <GiveUpButton on:click={giveUp}/>
    </div>
    <hr />
    <Keypad />
</div>
