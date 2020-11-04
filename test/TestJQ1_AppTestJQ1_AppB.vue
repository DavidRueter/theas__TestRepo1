<template>
    <b-container id="TestJQ1_Appvue" fluid="lg" style="padding: 0">

        <b-row no-gutters fluid>
            <b-col cols="12">
                <h3>Bust that cache again! Maybe...</h3>
                <p>Hello World</p>

                <p>Scanner goes here</p>
                <QRScan></QRScan>
            </b-col>
        </b-row>

        <b-row no-gutters>
            <b-col cols="12">
               <TestBSVTable></TestBSVTable>
            </b-col>
        </b-row>

    <b-row no-gutters>

    <b-col cols="3">
    <JqxBarGauge ref="barGaugeReference"
        width="100%"
        :values="values" :formatFunction="formatFunction">
    </JqxBarGauge>


    <JqxCalendar width="200"
                 :selectionMode="'range'" :value="value">
    </JqxCalendar>


    </b-col>

    <b-col cols="9">
    <JqxGrid ref="grid"
             width="100%" :source="dataAdapter"
             :columns="columns" :columnsresize="true"
             :pageable="true">
    </JqxGrid>
    </b-col>

    </b-row>
  <b-container>

</template>
 
<script>
    import JqxBarGauge from {{ '/cdn/jqw/jqwidgets-vue/vue_jqxbargauge.vue'|theasResource }};
    import JqxGrid from {{ '/cdn/jqw/jqwidgets-vue/vue_jqxgrid.vue'|theasResource }};
    import JqxCalendar from {{ '/cdn/jqw/jqwidgets-vue/vue_jqxcalendar.vue'|theasResource }};
    import QRScan from  {{ '/test/QRScan.vue'|theasResource }};
    import TestBSVTable from  {{ '/Test/TestBSVTable.vue'|theasResource }};

 
    export default {
        components: {
            JqxBarGauge,
            JqxGrid,
            JqxCalendar,
            QRScan,
            TestBSVTable
        },
        data: function () {
            return {
                values: [10, 20, 30, 40, 50],

                value: new Date(2016, 7, 7),

        dataAdapter: new jqx.dataAdapter(this.source),
        columns: [
            { text: 'Name', datafield: 'name', width: 250 },
            { text: 'Beverage Type', datafield: 'type', width: 250 },
            { text: 'Calories', datafield: 'calories', width: 180 },
            { text: 'Total Fat', datafield: 'totalfat', width: 120 },
            { text: 'Protein', datafield: 'protein', minwidth: 120 }
        ],

            }
        },

        beforeCreate: function () {            
            // Add here any data where you want to transform before components be rendered
            this.source = {
                datatype: 'json',
                datafields: [
                    { name: 'name', type: 'string' },
                    { name: 'type', type: 'string' },
                    { name: 'calories', type: 'int' },
                    { name: 'totalfat', type: 'string' },
                    { name: 'protein', type: 'string' }
                ],
                id: 'id',
                url: 'sampledata/beverages.txt'
            };
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
