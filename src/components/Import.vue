<template>
    <div>
        <div class="form-group">
            <input class="form-control" v-el:import type="file">
        </div>

        <button @click.prevent="onSubmit" :class="buttonClass">Import CSV</button>

        <div class="btn-group pull-right" role="group" aria-label="Import Options">
            <button @click="header = ! header" type="button" class="btn btn-default" :class="{active:header}" title="Use 1st Row as Header">Header</button>
        </div>
    </div>
</template>

<script>
    var Papa = require('papaparse')

    export default {

        props: {
            parsed: {
                twoWay: true
            }
        },

        data () {
            return {
                header: true
            }
        },

        methods: {
            onSubmit () {
                this.parsed = Papa.parse(this.$els.import.files[0], {
                    header: this.header,
                    complete: this.onParseComplete,
                    error: this.onParseError
                })
            },

            onParseError (error, file, inputElem, reason) {
                console.warn(error, file, inputElem, reason)
            },

            onParseComplete (results) {
                this.parsed = results
            }
        },

        computed: {
            buttonClass () {
                return {
                    'btn': true,
                    'btn-default': 'true'
                }
            }
        }
    }
</script>