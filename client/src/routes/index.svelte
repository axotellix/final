
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: extensions ]
    import { createPDF, openPDF } from '$lib/pdf-lib.js';
    import { renderCanvas } from '$lib/renderCanvas.js';

    // [ IMPORTS: system ]
    import { fade } from 'svelte/transition'
    import { onMount } from 'svelte';

    // [ IMPORTS: components ]
    import Analytics from '../components/Analytics.svelte';
    import ProcessSchedule from '../components/ProcessSchedule.svelte';


    // [ PROPS ]
    let acceptance_complete = false;
    const analytics = {
        defects:     true,       // has defects / no defects
        defect_rate: 0.15,       // percentage
        invoice:     1200000,    // price of no-defect cargo
    }


    // [ HOOKS ]
    onMount(() => {
        renderCanvas();
    });

</script>


<!-- [ TEMPLATE: Monitoring ] -->
<svelte:head>
    <title>Monitoring</title>
</svelte:head>

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'monitoring'>

    <!-- [ section: zone tabs ] -->
    <ul class = 'zone-tabs'>
        <li class="tab active"><a href = '/'>Зона А</a></li>
        <li class="tab"><a href = 'zoneB'>Зона Б</a></li>
        <li class="tab"><a href = 'zoneC'>Зона В</a></li> 
    </ul>

    <!-- [ section: dashboard ] -->
    <div class="dashboard">

        <!-- process info -->
        <p class = 'process-info'>
            <span class = 'supplier'>ООО Белкин и Стрелкин</span>
            Приемка: гречка, 15 тонн
        </p>

        <!-- video canvas & analytics -->
        <div class="monitor">
            <div class="video">
                <iframe src="https://player.vimeo.com/video/671962779?h=f5f328eef6&controls=0&muted=1&autoplay=1&loop=1" width="640" height="1138" frameborder="0" allow="autoplay" allowfullscreen></iframe>
            </div>
            <Analytics { analytics } />
        </div>

        <!-- button: complete acceptance -->
        {#if !acceptance_complete}
            <button on:click|preventDefault={ () => { acceptance_complete = true ; createPDF() } } class="CTA complete-acceptance">завершить приемку</button>
        {:else}
            <div class="hidden-area">
                <a href = '' on:click={ openPDF } class="CTA bg-orange make-invoice view-pdf">выставить счет</a>
                <a href = 'suppliers-overview' class="CTA order">дозаказать</a>
            </div>
        {/if}

    </div>

    <!-- [ section: process schedule ] -->
    <ProcessSchedule />

</main>
