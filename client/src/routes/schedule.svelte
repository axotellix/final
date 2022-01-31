
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: components ]
    import { fade } from 'svelte/transition'

</script>


<!-- [ TEMPLATE: Schedule ] -->
<svelte:head>
    <title>Schedule</title>
</svelte:head>

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'schedule'>
    <h1 class = 'page-title'>Schedule page</h1>

    <ul class = 'schedule-wrapper'>
        <li class = 'schedule-note'><span class = 'badge'>09:00</span> прием гречки (ООО Увелка)</li>
        <li class = 'schedule-note'><span class = 'badge'>09:00</span> прием гречки (ООО Увелка)</li>
        <li class = 'schedule-note'><span class = 'badge'>09:00</span> прием гречки (ООО Увелка)</li>
        <li class = 'schedule-note'><span class = 'badge'>09:00</span> прием гречки (ООО Увелка)</li>
    </ul>
</main>
