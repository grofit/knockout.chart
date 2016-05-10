# Knockout.Chart

A simple binding to let knockoutjs and chartjs (2.x version) come together for the greater good.

It supports the basic graph types and should work with any custom ones.

One major reason why this is a good idea is because this way you do not need your view model
knowing about your DOM elements, as the binding takes care of that, so you just expose
the meaningful stuff.

## Usage
The binding expects a type element describing what type of chart you want and the data you wish to expose:
```
<canvas data-bind="chart: { type: 'bar', data: myData }"></canvas>
```

Or it can be called with a options if you require more control over the chart:
```
<canvas data-bind="chart: { type: 'pie', data: myData, options: { segmentShowStroke: true, segmentStrokeColor: '#fff', segmentStrokeWidth: 2 } }"></canvas>
```

Or you can tell it to listen to knockout changes:
```
<canvas data-bind="chart: { type: 'pie', data: myData, options: { observeChanges: true, throttle: 100 } }"></canvas>
```


The chartjs specific options can be found here:

http://www.chartjs.org/docs/#line-chart-chart-options
http://www.chartjs.org/docs/#bar-chart-chart-options
http://www.chartjs.org/docs/#radar-chart-chart-options
http://www.chartjs.org/docs/#polar-area-chart-chart-options
http://www.chartjs.org/docs/#doughnut-pie-chart-chart-options

The bindings are:

* **type** - The type of chart you want, i.e. Pie, Bar, Doughnut etc, make sure the caps matches or it will blow up
* **data** - The data you want to put in, should match the desired format of data in the ChartJS documentation, observables will be translated for you
* **options** - The options based upon the ChartJS options documented above, there are a couple of unique ones which we use
 * **observeChanges** - This option tells the binding to scan for observables in the data and refresh the chart when they change
 * **throttle** - This option tells the binding to throttle updates by the desired amount, defaults to 100

## Possible Todos

I would like to get the legend being included via a template so you can split that out as well as maybe make the
data integration a bit more intelligent so we can just update the existing grid without constantly re-building it.

Here is an example of what it does and how to use it.
[View Example](https://rawgithub.com/grofit/knockout.chart/master/example.html)