
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: components ]
    import { fade } from 'svelte/transition'

</script>


<!-- [ TEMPLATE: Documents ] -->
<svelte:head>
    <title>Documents</title>
</svelte:head>

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'documents'>
    <h1>Мои документы</h1>

    <ul>
        <li class = 'body-text'>Паспорт на сырье <button class = 'CTA'>открыть</button></li>
        <li class = 'body-text'>Товарно-траспортная накладная <button class = 'CTA'>открыть</button></li>
        <li class = 'body-text'>Акт приема сырья <button class = 'CTA'>открыть</button></li>
        <li class = 'body-text'>Счет-фактура <button class = 'CTA'>открыть</button></li>
    </ul>
</main>
