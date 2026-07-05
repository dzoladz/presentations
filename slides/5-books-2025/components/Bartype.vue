<template>
    <canvas :width="width" :height="height" :id="id"></canvas>
</template>

<script>

    export default {
        name: 'BarType',
        props: ['id','width','height','type','title','labels','data', 'fill', 'backgroundColor', 'borderColor', 'borderWidth'],
        mounted() {
            let ctx = document.getElementById(this.id).getContext('2d');
            new Chart(ctx, {
                type: this.type ? this.type : 'bar',
                data: {
                    labels: this.labels,
                    datasets: [{
                        label: this.title,
                        data: this.data,
                        fill: this.fill,
                        backgroundColor: this.backgroundColor,
                        borderColor: this.borderColor,
                        borderWidth: this.borderWidth ? this.borderWidth : 1
                    }]
                }
            });
        }
    }
</script>