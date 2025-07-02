<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Solar Storm – Power Grid Monitoring</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #0e1117;
            color: white;
            font-family: 'Roboto Mono', monospace;
            margin: 0;
            padding: 20px;
        }
        h2 {
            text-align: center;
        }
        .grid {
            display: grid;
            grid-template-columns: 1.5fr 2.5fr 1.5fr;
            gap: 20px;
            margin-bottom: 30px;
        }
        .section, .box {
            background-color: #1f1f1f;
            padding: 15px;
            border-radius: 8px;
        }
        .chart-row {
            display: flex;
            gap: 20px;
            margin-bottom: 30px;
        }
        .chart {
            flex: 1;
            background-color: #1f1f1f;
            padding: 15px;
            border-radius: 8px;
        }
        .bottom-row {
            display: flex;
            gap: 20px;
        }
        img {
            width: 100%;
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <h2>SOLAR STORM – POWER GRID MONITORING</h2>

    <div class="grid">
        <div class="section">
            <h3 style="color: orange;">SOLAR STORM (G3 STRONG)</h3>
            <p><strong>Kp index:</strong> 7</p>
            <p><strong>Expected:</strong> 8:00 PM – 3:00 AM</p>
            <p><strong>Solar wind speed:</strong> 709 km/s</p>
            <p><strong>Density:</strong> 18.5 p/cm³</p>
            <p><strong>Bz:</strong> -15 nT</p>
            <p style="color: orange;"><strong>ALERT</strong></p>
        </div>

        <div class="section">
        <div id="dashboard-map" style="height: 300px;"></div>
        </div>

        <div class="section">
            <h3>OPERATIONAL RECOMMENDATIONS</h3>
            <ul>
                <li>Reduce loading on high-risk transformers</li>
                <li>Adjust transformer taps to limit GIC</li>
                <li>Consider delaying planned maintenance</li>
            </ul>
        </div>
    </div>

    <div class="chart-row">
        <div class="chart">
            <h4>Transformer GIC</h4>
            <div id="gic-chart" style="height: 300px;"></div>
        </div>
        <div class="chart">
            <h4>Voltage Stability</h4>
            <div id="voltage-chart" style="height: 300px;"></div>
        </div>
    </div>

    <div class="bottom-row">
        <div class="chart">
            <h4>Risk Levels</h4>
            <div id="risk-level-chart" style="height: 300px;"></div>
        </div>
        <div class="chart">
            <h4>Substation Status</h4>
            <p><strong>Gridport Sub:</strong> High</p>
            <p><strong>Maple Sub 85:</strong> Trap rot: 134 °F</p>
            <p><strong>Elmwood Sub 43:</strong> GIC 63 A</p>
        </div>
    </div>
<script>
    var gicData = {
        x: [1, 2, 3, 4, 5, 6, 7, 8],
        y: [30, 35, 33, 36, 40, 42, 45, 47],
        type: 'scatter',
        mode: 'lines+markers',
        line: {color: 'orange'}
    };

    Plotly.newPlot('gic-chart', [gicData], {
        paper_bgcolor: '#1f1f1f',
        plot_bgcolor: '#1f1f1f',
        font: {color: 'white'},
        margin: { t: 30, b: 40 }
    });
</script>
</body>
</html>
