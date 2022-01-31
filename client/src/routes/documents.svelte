
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
    <h1 class = 'page-title'>Мои документы</h1>

    <ul class = 'documents-wrapper'>
        <li class = 'doc'>Паспорт на сырье <button class = 'CTA'>открыть</button></li>
        <li class = 'doc'>Товарно-траспортная накладная <button class = 'CTA'>открыть</button></li>
        <li class = 'doc'>Акт приема сырья <button class = 'CTA'>открыть</button></li>
        <li class = 'doc'>Счет-фактура <button class = 'CTA'>открыть</button></li>
    </ul>
</main>
