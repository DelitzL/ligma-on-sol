<template>
    <div class="updatetitle">
        <h1>Crypto Blog</h1>
        <h2>Ligma Coin Price Analysis</h2>
    </div>
    <iframe id="dextools-widget"
        title="DEXTools Trading Chart"
        class="full-width-iframe"
        src="https://www.dextools.io/widget-chart/en/solana/pe-light/3UNN3bQDRUGXHwUpEupyojxRKiXy2Pvb8m5rwW1ZKKSr?theme=light&chartType=2&chartResolution=30&drawingToolbars=false">
    </iframe>
    <!--subscription to get the Required API key to function properly: https://developer.dextools.io/products/http-api/Documentation#overview-->
</template>

<style scoped>
    .updatesection {
        padding: 50px;
    }

    .updatetitle {
        padding: 50px;
    }

    .full-width-iframe {
        width: 100%;      
        height: 80%;     
        border: none;      
    }
</style>