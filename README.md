# First-start
My first repository 
<br>
Author- Swarik Swaraj 
function createLineChart(canvasId, labels, datasets) {
    const ctx = document.getElementById(canvasId).getContext('2d');
    return new Chart(ctx, {
        type: 'line',
        data: {
            labels: labels,
            datasets: datasets.map((ds, i) => ({
                label: ds.label,
                data: ds.data,
                borderColor: COLORS[i % COLORS.length],
                backgroundColor: COLORS[i % COLORS.length] + '20',
                borderWidth: 2,
                fill: ds.fill || false,
                tension: 0.3,
                pointRadius: 3,
                pointHoverRadius: 6,
            }))
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            interaction: {
                mode: 'index',
                intersect: false,
            },
            plugins: {
                legend: {
                    position: 'top',
                    labels: { usePointStyle: true, padding: 20 }
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            return `${context.dataset.label}: ${formatValue(context.parsed.y, 'currency')}`;
                        }
                    }
                }
            },
            scales: {
                x: {
                    grid: { display: false }
                },
                y: {
                    beginAtZero: true,
                    ticks: {
                        callback: function(value) {
                            return formatValue(value, 'currency');
                        }
                    }
                }
            }
        }
    });
}
