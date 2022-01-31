
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: extensions ]
    import { renderCanvas } from '$lib/renderCanvas.js';

    // [ IMPORTS: components ]
    import CircleProgress from '../components/CircleProgress.svelte';

    // [ IMPORTS: system modules ]
    import { fade } from 'svelte/transition'
    import { onMount } from 'svelte';

    const analytics = {
        defects:     true,       // has defects / no defects
        defect_rate: 15,         // percentage
        invoice:     1200000,    // price of no-defect cargo
    }

    const supliers = new Array(4).fill(0)

    const randData = ( datatype ) => {
        if( datatype == 'defect-rate' ) {

            const max = 20
            const min = 4
            return Math.floor(Math.random() * (max - min + 1)) + min 

        } else if( datatype == 'company' ) {

            const companies = ['ООО Белкин и Стрелкин', 'ОАО Россельхоз', 'ЗАО КолоссОК']
            const max = companies.length - 1
            const min = 0
            let index = Math.floor(Math.random() * (max - min + 1)) + min 
            return companies[index]

        } else if( datatype == 'city' ) {

            const cities = ['Тюмень', 'Красноярск', 'Челлябинск']
            const max = cities.length - 1
            const min = 0
            let index = Math.floor(Math.random() * (max - min + 1)) + min 
            return 'г. ' + cities[index]

        } else if( datatype == 'time' ) {

            const times = [1, 2, 3, 4]
            const max = times.length - 1
            const min = 0
            let index = Math.floor(Math.random() * (max - min + 1)) + min 
            return  times[index] + ' час'

        }
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

<main in:fade='{{ duration: 100 }}' out:fade|local='{{ duration: 100 }}' class = 'suppliers-overview'>

    <!-- [ section: recommended suppliers ] -->
    <section class="recommended-suppliers suppliers">

        <!-- title -->
        <div class="title">
            <p class="title">Рекомендованные поставщики</p>
        </div>

        <!-- supplier cards -->
        <div class="supplier-cards">

            {#each supliers as suplier }
                <div class="supplier-card">
                    <!-- supplier info -->
                    <div class="supplier-info">
                        <p class="supplier-title">
                            <span class = 'city'>{ randData('city') }</span>
                            { randData('company') }
                        </p>

                        <p class="supplier-metrics">
                            <span class = 'cargo-price'>₽ 1 200 000 / т</span>
                            <span class = 'cargo-price'><b>350 тонн</b> в наличии</span>
                            <span class = 'cargo-price'>постоплата</span>
                        </p>

                        <div class="time-badge badge">
                            { randData('time') }
                        </div>
                    </div>

                    <!-- supplier info -->
                    <div class="defect-rate">
                        <div class="estimation">
                            <CircleProgress size = { 100 } stroke = { 7 } value = { randData('defect-rate') } />
                            <p class="caption">Процент брака</p>
                        </div>
                        <button class="CTA-small select">связаться</button>
                    </div>
                </div>
            {/each}

    </section>

    <!-- [ section: rest suppliers ] -->
    <section class="rest-suppliers suppliers">

        <!-- title -->
        <div class="title">
            <p class="title">Прочие поставщики</p>
        </div>

        <!-- supplier cards -->
        <div class="supplier-cards">

            {#each supliers as suplier }
                <div class="supplier-card">
                    <!-- supplier info -->
                    <div class="supplier-info">
                        <p class="supplier-title">
                            <span class = 'city'>{ randData('city') }</span>
                            { randData('company') }
                        </p>

                        <p class="supplier-metrics">
                            <span class = 'cargo-price'>₽ 1 200 000 / т</span>
                            <span class = 'cargo-price'><b>350 тонн</b> в наличии</span>
                            <span class = 'cargo-price'>постоплата</span>
                        </p>

                        <div class="time-badge badge">
                            { randData('time') }
                        </div>
                    </div>

                    <!-- supplier info -->
                    <div class="defect-rate">
                        <div class="estimation">
                            <CircleProgress size = { 100 } stroke = { 7 } value = { randData('defect-rate') } />
                            <p class="caption">Процент брака</p>
                        </div>
                        <button class="CTA-small select">связаться</button>
                    </div>
                </div>
            {/each}

        </div>

    </section>

</main>
