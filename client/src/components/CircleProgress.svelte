
<!-- [ SCRIPTS ] -->
<script>

    // [ PROPS ]
    export let value = 0;
    export let size = 150;
    export let stroke = 10;

    // [ MAIN ]
    let radius = size / 2;
    let len = 2 * radius * Math.PI;
    let da = len;

    //0 to 100
    $: setProgress( value );

    function setProgress(percent) {
        value = len - (percent / 100) * len;
    }

</script>


<!-- [ TEMPLATE ] -->
<div class="circle-progress" style = "width: {size + stroke}px; height: {size + stroke}px" data-progress = { Math.round((da - value) * 100 / da) }>

    <svg viewbox="0 0 {size + stroke} {size + stroke}">
        <circle r="{ size / 2 }" cx="{ size / 2 + stroke / 2 }" cy="{ size / 2 + stroke / 2 }" stroke-width = { stroke } class="track"></circle>
        <circle stroke-dasharray = { da } stroke-dashoffset = { value } r="{ size / 2 }" cx="{ size / 2 + stroke / 2 }" cy="{ size / 2 + stroke / 2 }" stroke-width = { stroke } class="progress"></circle>
    </svg>
    
</div>