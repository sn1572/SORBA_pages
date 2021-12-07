<html>
<head>
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">
    google.charts.load('current', {'packages':['gantt']});
    google.charts.setOnLoadCallback(drawChart);

    function daysToMilliseconds(days) {
        return days * 24 * 60 * 60 * 1000;
    }

    function drawChart() {

        var data = new google.visualization.DataTable();
        data.addColumn('string', 'Task ID');
        data.addColumn('string', 'Task Name');
        data.addColumn('string', 'Resource');
        data.addColumn('date', 'Start Date');
        data.addColumn('date', 'End Date');
        data.addColumn('number', 'Duration');
        data.addColumn('number', 'Percent Complete');
        data.addColumn('string', 'Dependencies');

        data.addRows([
            ['RB-refresh',          <!-- ID -->
             'R&B Refresh',         <!-- Name -->
             'ez17',                <!-- Resource used -->
             new Date(2022, 0, 1),  <!-- Start date -->
             new Date(2022, 3, 1),  <!-- End date -->
             null,                  <!-- Duration -->
             60,                    <!-- Percent complete -->
             null],                 <!-- Dependencies (Task ID) -->
            ['RR-refresh',
             'R&R Refresh',
             'ez17',
             new Date(2022, 3, 1),
             new Date(2022, 9, 1),
             null,
             0,
             'RB-refresh'],
            ['Gnarnia-layout',
             'Gnarnia layout',
             'hand-tools',
             new Date(2022, 0, 1),
             new Date(2022, 2, 1),
             null,
             0,
             null],
            ['Gnarnia-cut', 'Cut Gnarnia trail', 'hand-tools',
             new Date(2022, 2, 2),
             new Date(2022, 6, 1),
             null, 0, 'Gnarnia-layout'],
            ['Gnarnia-bench', 'Gnarnia climb trail maintanence', 'hand-tools',
             new Date(2021, 12, 18),
             new Date(2022, 2, 1),
             null, 0, null]
        ]);

        var options = {
            height: 275
        };

        var chart = new google.visualization.Gantt(document.getElementById('chart_div'));

        chart.draw(data, options);
    }
    </script>
</head>
<body>
    <div id="chart_div"></div>
</body>
</html>
