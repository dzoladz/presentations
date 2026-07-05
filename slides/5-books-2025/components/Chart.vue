<template>
  <Bar :data="chartData" :options="chartOptions" />
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

const data = {
  labels: [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
    'July',
    'August',
    'September',
    'October',
    'November',
    'December'
  ],
  datasets: [
    {
      label: 'Data One',
      backgroundColor: '#a8f879',
      borderColor: '#FF6384',
            barThickness: 30,
            borderWidth: 2,
            borderRadius: 20, // This will round the corners
            borderSkipped: false, // To make all side rounded
      data: [40, 20, 12, 39, 10, 40, 39, 80, 40, 20, 12, 11]
    }
  ]
}

const options = {
  responsive: true,
  maintainAspectRatio: false,
  indexAxis: 'x',  // 'x' for vertical; 'y' for horizontal
  scales: {
    x: {
      title: {
        display: true,
        text: 'Month',
        color: '#911',
        font: {
          family: 'Open Sans',
          size: 20,
          weight: 'bold',
          lineHeight: 1.2,
        },
      },
    },
    y: {
      title: {
          display: true,
          text: 'Month',
          color: '#911',
          font: {
            family: 'Open Sans',
            size: 20,
            weight: 'bold',
            lineHeight: 1.2,
          },
          padding: {top: 20, left: 0, right: 0, bottom: 0}
        },
      beginAtZero: true,
      grid: {
        display: true,
        color: '#777777',
        drawOnChartArea: true,
        drawTicks: true,
      },
      ticks: {
        display: true,
        z: 0,
        color: '#bcbcbc',
        padding: 5,
        font: {
          size: 20,
          weight: 'bold',
          lineHeight: 1.1,
        }
      }
    }
  },
  plugins: {
    title: {  // https://www.chartjs.org/docs/latest/configuration/title.html
      display: false,
      text: 'Title goes here ...',
      color: '#0055ff',
      position: 'top',
      fullSize: true,
      padding: 10,
      align: 'start',
      font: {
        family: 'Arial',
        size: 30,
        weight: 'bold',
        style: 'italic',
        lineHeight: 2.0
      }
    },
    legend: {
      display: false,
      align: 'center',
      position: 'bottom',
    },
    tooltip: {
      enabled: false
    },
  },
  animations: {
      tension: {
        duration: 1000,
        easing: 'linear',
        from: 1,
        to: 0,
        loop: true
      }
  }
}

export default {
  name: 'BarChart',
  components: { Bar },
  props: ['data'],
  data() {
    return {
      chartData: data,
      chartOptions: options
    }
  }
}


</script>