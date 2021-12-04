
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
    <h1>Schedule page</h1>

    <ul>
        <li class = 'body-text'>09:00 прием гречки (ООО Увелка)</li>
        <li class = 'body-text'>09:00 прием гречки (ООО Увелка)</li>
        <li class = 'body-text'>09:00 прием гречки (ООО Увелка)</li>
        <li class = 'body-text'>09:00 прием гречки (ООО Увелка)</li>
    </ul>
</main>
