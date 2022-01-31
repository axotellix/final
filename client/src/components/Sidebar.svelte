
<!-- [ SCRIPT ] -->
<script>

    // [ IMPORTS: stores ]
    import NavStore from '../stores/NavStore.js';

    // [ IMPORTS: system ]
    import { onMount } from 'svelte';

    // [ FUNCTIONS ]
    const updateActive = ( route ) => {
        NavStore.update(() => {
			return route;
		});
    }

    // [ HOOKS ]
    onMount(() => {
        
        // get > image analytics from URI
        const url = window.location.href
        let page = 'monitoring'
        if( url.indexOf('documents') > 0 ) page = 'documents'
        if( url.indexOf('notifications') > 0 ) page = 'notifications'
        if( url.indexOf('schedule') > 0 ) page = 'schedule'
        
        NavStore.update(() => {
			return page;
		});
    
    });



</script>


<!-- [ TEMPLATE: Sidebar > __layout ] -->
<aside>

    <!-- section: logo -->
    <p class="logo">Кабинет<br />предприятия</p>

    <!-- section: nav -->
    <nav>
        <a href="/"              on:click={ () => { updateActive('monitoring') } } class="nav-link {$NavStore === 'monitoring' ? 'active' : ''}" >мониторинг</a>
        <a href="/schedule"      on:click={ () => { updateActive('schedule') } } class="nav-link {$NavStore === 'schedule' ? 'active' : ''}">расписание</a>
        <a href="/notifications" on:click={ () => { updateActive('notifications') } } class="nav-link {$NavStore === 'notifications' ? 'active' : ''}">уведомления</a>
        <a href="/documents"     on:click={ () => { updateActive('documents') } } class="nav-link {$NavStore === 'documents' ? 'active' : ''}">документы</a>
    </nav>

    <!-- section: reminder -->
    <div class="reminder">

        <div class="time-badge badge">
            <p>17:40</p>
        </div>

        <p class = 'title'>Прием гречки</p>
        <p class = 'supplier'>ООО Белкин и Стрелкин</p>

    </div>

</aside>
