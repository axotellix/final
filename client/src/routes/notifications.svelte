
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
    <h1 class = 'page-title'>Уведомления</h1>

    <ul class = 'notifications-wrapper'>
        <li class = 'notification complete'>
            <p class = 'notification-msg'>
                <span class = 'notification-title'>12:00 разгрузка завершена:</span>
                ООО Увелка (гречка, 25 тонн)
            </p>
        </li>
    </ul>
</main>
