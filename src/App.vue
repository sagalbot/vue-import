<style>
    html, body, #app {
        height: 100%;
    }

    #app {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }

    .flexed {
        width: 50%;
    }

    pre {
        /*background: none;*/
        /*border: none;*/
        border-top: 1px solid rgba(50, 50, 50, .25);
        border-bottom: 1px solid rgba(50, 50, 50, .25);
        margin-top: 3em;
        max-height: 400px;
        overflow: scroll;
    }
</style>

<template>
    <div id="app" class="container">
        <div class="flexed">
            <pre>{{ import | json }}</pre>
        </div>

        <div class="flexed">
            <import :parsed.sync="import"></import>
        </div>
    </div>
</template>

<script>
    import Import from './components/Import'

    export default {
        components: {
            Import
        },

        data () {
            return {
                import: null
            }
        }
    }
</script>
