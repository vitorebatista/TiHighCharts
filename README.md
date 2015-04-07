# Alloy TiHighCharts Widget [![Appcelerator Titanium](http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png)](http://appcelerator.com/titanium/) [![Appcelerator Alloy](http://www-static.appcelerator.com/badges/alloy-git-badge-sq.png)](http://appcelerator.com/alloy/)

## Overview
This is a widget for the [Alloy](http://projects.appcelerator.com/alloy/docs/Alloy-bootstrap/index.html) MVC framework of [Appcelerator](http://www.appcelerator.com)'s [Titanium](http://www.appcelerator.com/platform) platform.

The widget provides a simple loading mask that can be easily styled and configured.

## Screenshot
![TiHighCharts](https://raw.github.com/vitorebatista/TiHighCharts/master/docs/screenshot.png)

## Usage [![gitTio](http://gitt.io/badge.png)](http://gitt.io/component/TiHighCharts)

1. Install [this widget](http://gitt.io/component/TiHighCharts) via [gitTio](http://gitt.io):

	`gittio install TiHighCharts`
	
2. In your `app/views/index.xml` use it like this:
	```
<Alloy>
	<TabGroup backgroundColor="white" >
	    <Tab title="Polar Spider">
	        <Window title="Polar-Spider Chart">
	        	<ScrollableView>
	            	<Widget src="com.veb.tihighcharts" id="polar_spider_chart"/>
	            </ScrollableView>
	        </Window>
	    </Tab>
		<Tab title="Line">
	        <Window title="Line Chart">
	        	<ScrollableView>
	            	<Widget src="com.veb.tihighcharts" id="line_chart"/>
	            </ScrollableView>
	        </Window>
	    </Tab>
	    <Tab title="Pie" >
	        <Window title="Pie Chart">
				<ScrollableView>
	           		<Widget src="com.veb.tihighcharts" id="pie_chart"/>
	           	</ScrollableView>
	        </Window>
	    </Tab>
	</TabGroup>
</Alloy>
	```
3. In your `app/controllers/index.js` use it like this:
 	```


$.pie_chart.loadChart('PIE',{
		            chart: {
		            	renderTo: 'container',
		                plotBackgroundColor: null,
		                plotBorderWidth: null,
		                plotShadow: false
		            },
		            title: {
		                text: 'Browser market shares at a specific website, 2010'
		            },
		            tooltip: {
		        	    pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
		            },
		            plotOptions: {
		                pie: {
		                    allowPointSelect: true,
		                    cursor: 'pointer',
		                    dataLabels: {
		                        enabled: false
		                    },
		                    showInLegend: false
		                }
		            },
		            series: [{
		                type: 'pie',
		                name: 'Browser share',
		                data: [
		                    ['Firefox',   25.0],
		                    ['IE',       26.8],
		                    {
		                        name: 'Chrome',
		                        y: 32.8,
		                        sliced: false,
		                        selected: false
		                    },
		                    ['Safari',    5.5],
		                    ['Opera',     6.2],
		                    ['Others',   3.7]
		                ]
		            }]
		        });

$.line_chart.loadChart('LINE',{
	
		chart: {
        	renderTo: 'container',
        	plotBackgroundColor: null,
            plotBorderWidth: null,
            plotShadow: false,
            type: 'line'
        },	
        title: {
            text: 'Monthly Average Temperature',
            x: -20 //center
        },
        subtitle: {
            text: 'Source: WorldClimate.com',
            x: -20
        },
        xAxis: {
            categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
        },
        yAxis: {
            title: {
                text: 'Temperature (°C)'
            },
            plotLines: [{
                value: 0,
                width: 1,
                color: '#808080'
            }]
        },
        tooltip: {
            valueSuffix: '°C'
        },
        legend: {
            layout: 'vertical',
            align: 'right',
            verticalAlign: 'middle',
            borderWidth: 0
        },
        series: [{
            name: 'Tokyo',
            data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
        }, {
            name: 'New York',
            data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
        }, {
            name: 'Berlin',
            data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
        }, {
            name: 'London',
            data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
        }]
    });


$.polar_spider_chart.loadChart('POLAR-SPIDER',{

        chart: {
        	renderTo: 'container',
            polar: true,
            type: 'line'
        },

        title: {
            text: 'Budget vs spending',
        },

        pane: {
            size: '70%'
        },

        xAxis: {
            categories: ['Sales', 'Marketing', 'Development', 'Customer Support',
                    'Information Technology', 'Administration'],
            tickmarkPlacement: 'on',
            lineWidth: 0
        },

        yAxis: {
            gridLineInterpolation: 'polygon',
            lineWidth: 0,
            min: 0
        },

        tooltip: {
            shared: true,
            pointFormat: '<span style="color:{series.color}">{series.name}: <b>${point.y:,.0f}</b><br/>'
        },

        legend: {
            align: 'center',
            verticalAlign: 'top',
            y: 70,
            layout: 'horizontal'
        },

        series: [{
            name: 'Allocated Budget',
            data: [43000, 19000, 60000, 35000, 17000, 10000],
            pointPlacement: 'on'
        }, {
            name: 'Actual Spending',
            data: [50000, 39000, 42000, 31000, 26000, 14000],
            pointPlacement: 'on'
        }, {
            name: 'xxx Spending',
            data: [10300, 19000, 22000, 91000, 26000, 14000],
            pointPlacement: 'on'
        }]

    });


$.index.open();

	```



## Changelog
* 1.0
  * Initial version
