
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


    // [ PRESETS ]
    const api    = 'http://rsandrey.pythonanywhere.com/'
    const server = 'https://final-server-axotellix.vercel.app/'


    // [ PROPS ]
    let extra_analytics_requested  = false;
    let analytics_received         = false;
    let acceptance_complete        = false;

    const analytics = {
        status:      'good',      // has defects / no defects
        percent:     0,           // percentage
        invoice:     0,           // price of no-defect cargo
    }


    // [ HOOKS ]
    onMount(() => {
        
        // get > image analytics from URI
        const urlParams = new URLSearchParams(window.location.search);
        let status = urlParams.get('status');
        let percent = urlParams.get('percent');
        
        if( status !== null && percent !== null) {
            analytics.status  = status
            analytics.percent = percent
            console.log(analytics.percent);
            analytics.invoice = 2100205
            analytics_received = true
            api = api
        }

        renderCanvas(analytics.percent);

    });


</script>


<!-- [ TEMPLATE: Monitoring ] -->
<svelte:head>
    <title>Monitoring</title>
</svelte:head>

<!-- modal: image analytics -->
{#if extra_analytics_requested}
    <div class="modal-result">
        <div class="overlay" on:click={ () => { analytics_received = false } }></div>
        <div class="message">
            <h5 class="title">Результаты анализа:</h5>
            <div class="content">
                <p>{ 'status  = ' + analytics.status  }</p>
                <p>{ 'percent = ' + analytics.percent }</p>
            </div>
        </div>
    </div>
{/if}

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'monitoring'>

    <!-- [ section: zone tabs ] -->
    <ul class = 'zone-tabs'>
        <li class="tab"><a href = '/'>Зона А</a></li>
        <li class="tab active"><a href = 'zoneB'>Зона Б</a></li>
        <li class="tab"><a href = 'zoneC'>Зона В</a></li>
    </ul>

    <!-- [ section: dashboard ] -->
    <div class="dashboard">

        <!-- process info -->
        <p class = 'process-info'>
            <span class = 'supplier'>ООО Трио</span>
            Приемка: овес, 20 тонн
        </p>

        <!-- video canvas & analytics -->
        <div class="monitor">
            <div class="video { analytics_received ? 'uploaded' : '' }">
                {#if analytics_received}
                    <img src="{api + 'res.png'}" class = 'uploaded-img' alt="uploaded img">
                {/if}
                <form method="post" class = 'upload-form' enctype="multipart/form-data" action = '{server + 'upload'}'>
                    <p class = 'description'>Загрузите изображение, чтобы проанализировать его</p>
                    <input type = 'file' name = 'img' class = 'CTA bg-orange' />
                    <button type = 'submit' name = 'submit' class = 'CTA bg-orange upload'>анализ</button>
                </form>
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
