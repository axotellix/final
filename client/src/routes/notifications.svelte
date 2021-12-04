
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: components ]
    import { fade } from 'svelte/transition'

</script>


<!-- [ TEMPLATE: Notifications ] -->
<svelte:head>
    <title>Notifications</title>
</svelte:head>

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'notifications'>
    <h1>Уведомления</h1>

    <p>разгрузка завершена: ООО Увелка (гречка, 25 тонн)</p>
</main>
