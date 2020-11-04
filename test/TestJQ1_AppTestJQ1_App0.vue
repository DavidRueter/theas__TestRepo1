<template>
  <div>
  <p>Hello World</p>

    <JqxBarGauge ref="barGaugeReference"
        :width="600" :height="600" 
        :values="values" :formatFunction="formatFunction"
    >
    </JqxBarGauge>

  </div>
</template>
 
<script>
    import JqxBarGauge from '/cdn/jqw/jqwidgets-vue/vue_jqxbargauge.vue';
 
    export default {
        components: {
            JqxBarGauge
        },
        data: function () {
            return {
                values: [10, 20, 30, 40, 50],

            }
        },


        methods: {
            formatFunction: function (value, index, color) {
                return color;
            },

        }
    }
</script>

<style>
    h1   {color: blue;}
    p    {color: red;}    
</style>
