### Advanced Tutorial: JavaScript Advanced Visualizations with D3.js

#### Introduction

D3.js is a powerful JavaScript library for creating complex and interactive data visualizations. This advanced tutorial will cover creating network graphs, heatmaps, and geospatial visualizations using D3.js. By mastering these techniques, you can build sophisticated visualizations for various business applications.

### Network Graphs

Network graphs are used to visualize relationships between entities. Each entity is represented as a node, and the connections between them are represented as links.

#### Example: Creating a Network Graph

**JavaScript**:
```javascript
<!DOCTYPE html>
<html>
<head>
    <title>Network Graph</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <style>
        .link {
            stroke: #999;
            stroke-opacity: 0.6;
        }
        .node circle {
            stroke: #fff;
            stroke-width: 1.5px;
        }
    </style>
</head>
<body>
    <h1>Network Graph</h1>
    <div id="network"></div>

    <script>
        // Sample data
        let graph = {
            nodes: [
                { id: 'Alice' },
                { id: 'Bob' },
                { id: 'Charlie' },
                { id: 'David' },
                { id: 'Eve' }
            ],
            links: [
                { source: 'Alice', target: 'Bob' },
                { source: 'Alice', target: 'Charlie' },
                { source: 'Bob', target: 'David' },
                { source: 'Charlie', target: 'David' },
                { source: 'David', target: 'Eve' }
            ]
        };

        // Set up SVG dimensions
        let width = 800;
        let height = 600;

        // Create SVG container
        let svg = d3.select('#network')
            .append('svg')
            .attr('width', width)
            .attr('height', height);

        // Create simulation
        let simulation = d3.forceSimulation(graph.nodes)
            .force('link', d3.forceLink(graph.links).id(d => d.id).distance(100))
            .force('charge', d3.forceManyBody().strength(-400))
            .force('center', d3.forceCenter(width / 2, height / 2));

        // Add links
        let link = svg.append('g')
            .attr('class', 'links')
            .selectAll('line')
            .data(graph.links)
            .enter().append('line')
            .attr('class', 'link');

        // Add nodes
        let node = svg.append('g')
            .attr('class', 'nodes')
            .selectAll('circle')
            .data(graph.nodes)
            .enter().append('circle')
            .attr('r', 10)
            .attr('fill', 'steelblue')
            .call(d3.drag()
                .on('start', dragstarted)
                .on('drag', dragged)
                .on('end', dragended));

        node.append('title')
            .text(d => d.id);

        // Update positions on each tick
        simulation.on('tick', () => {
            link
                .attr('x1', d => d.source.x)
                .attr('y1', d => d.source.y)
                .attr('x2', d => d.target.x)
                .attr('y2', d => d.target.y);

            node
                .attr('cx', d => d.x)
                .attr('cy', d => d.y);
        });

        // Drag functions
        function dragstarted(event, d) {
            if (!event.active) simulation.alphaTarget(0.3).restart();
            d.fx = d.x;
            d.fy = d.y;
        }

        function dragged(event, d) {
            d.fx = event.x;
            d.fy = event.y;
        }

        function dragended(event, d) {
            if (!event.active) simulation.alphaTarget(0);
            d.fx = null;
            d.fy = null;
        }
    </script>
</body>
</html>
```

**Explanation**:
- A sample graph is defined with nodes and links.
- The D3 force simulation is used to calculate the positions of the nodes and links dynamically.
- Nodes and links are added to the SVG container, and drag behavior is implemented for the nodes.

### Heatmaps

Heatmaps are used to represent data values as colors in a matrix.

#### Example: Creating a Heatmap

**JavaScript**:
```javascript
<!DOCTYPE html>
<html>
<head>
    <title>Heatmap</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <style>
        .cell {
            stroke: #ccc;
        }
    </style>
</head>
<body>
    <h1>Heatmap</h1>
    <div id="heatmap"></div>

    <script>
        // Sample data
        let data = [
            { day: 'Monday', hour: '1', value: 10 },
            { day: 'Monday', hour: '2', value: 20 },
            // Add more data points...
        ];

        let days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'];
        let hours = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12'];

        // Set up SVG dimensions
        let margin = { top: 50, right: 0, bottom: 100, left: 30 },
            width = 800 - margin.left - margin.right,
            height = 400 - margin.top - margin.bottom,
            gridSize = Math.floor(width / hours.length),
            legendElementWidth = gridSize * 2.5,
            buckets = 9,
            colors = ['#ffffd9', '#edf8b1', '#c7e9b4', '#7fcdbb', '#41b6c4', '#1d91c0', '#225ea8', '#253494', '#081d58'];

        // Create SVG container
        let svg = d3.select('#heatmap')
            .append('svg')
            .attr('width', width + margin.left + margin.right)
            .attr('height', height + margin.top + margin.bottom)
            .append('g')
            .attr('transform', `translate(${margin.left},${margin.top})`);

        // Create scales
        let dayLabels = svg.selectAll('.dayLabel')
            .data(days)
            .enter().append('text')
            .text(d => d)
            .attr('x', 0)
            .attr('y', (d, i) => i * gridSize)
            .style('text-anchor', 'end')
            .attr('transform', `translate(-6, ${gridSize / 1.5})`)
            .attr('class', 'dayLabel mono axis');

        let timeLabels = svg.selectAll('.timeLabel')
            .data(hours)
            .enter().append('text')
            .text(d => d)
            .attr('x', (d, i) => i * gridSize)
            .attr('y', 0)
            .style('text-anchor', 'middle')
            .attr('transform', `translate(${gridSize / 2}, -6)`)
            .attr('class', 'timeLabel mono axis');

        // Create heatmap cells
        let colorScale = d3.scaleQuantile()
            .domain([0, buckets - 1, d3.max(data, d => d.value)])
            .range(colors);

        let cards = svg.selectAll('.hour')
            .data(data, d => d.day + ':' + d.hour);

        cards.enter().append('rect')
            .attr('x', d => (d.hour - 1) * gridSize)
            .attr('y', d => days.indexOf(d.day) * gridSize)
            .attr('rx', 4)
            .attr('ry', 4)
            .attr('class', 'hour bordered')
            .attr('width', gridSize)
            .attr('height', gridSize)
            .style('fill', colors[0])
            .merge(cards)
            .transition()
            .duration(1000)
            .style('fill', d => colorScale(d.value));

        cards.exit().remove();

        // Add legend
        let legend = svg.selectAll('.legend')
            .data([0].concat(colorScale.quantiles()), d => d);

        legend.enter().append('g')
            .attr('class', 'legend')
            .append('rect')
            .attr('x', (d, i) => legendElementWidth * i)
            .attr('y', height)
            .attr('width', legendElementWidth)
            .attr('height', gridSize / 2)
            .style('fill', (d, i) => colors[i]);

        legend.enter().append('g')
            .attr('class', 'legend')
            .append('text')
            .attr('class', 'mono')
            .text(d => `≥ ${Math.round(d)}`)
            .attr('x', (d, i) => legendElementWidth * i)
            .attr('y', height + gridSize);

        legend.exit().remove();
    </script>
</body>
</html>
```

**Explanation**:
- Sample data is defined for a heatmap representing values for days and hours.
- SVG dimensions and scales are set up.
- Heatmap cells are created and colored

 based on data values.
- A legend is added to indicate the color scale.

### Geospatial Visualizations

Geospatial visualizations represent data on maps. D3.js can be combined with GeoJSON data to create these visualizations.

#### Example: Creating a Choropleth Map

**JavaScript**:
```javascript
<!DOCTYPE html>
<html>
<head>
    <title>Choropleth Map</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <style>
        .county {
            stroke: #fff;
            stroke-width: 0.5;
        }
        .legend {
            fill: #444;
            font-size: 12px;
        }
    </style>
</head>
<body>
    <h1>Choropleth Map</h1>
    <div id="map"></div>

    <script>
        // Set up SVG dimensions
        let width = 960;
        let height = 600;

        // Create SVG container
        let svg = d3.select('#map')
            .append('svg')
            .attr('width', width)
            .attr('height', height);

        // Load and process data
        Promise.all([
            d3.json('https://d3js.org/us-10m.v1.json'),
            d3.csv('population_data.csv', d => {
                return {
                    id: d.id,
                    population: +d.population
                };
            })
        ]).then(([us, populationData]) => {
            let populationById = {};
            populationData.forEach(d => { populationById[d.id] = d.population; });

            let colorScale = d3.scaleQuantize()
                .domain([0, d3.max(populationData, d => d.population)])
                .range(d3.schemeBlues[9]);

            let path = d3.geoPath();

            svg.append('g')
                .attr('class', 'counties')
                .selectAll('path')
                .data(topojson.feature(us, us.objects.counties).features)
                .enter().append('path')
                .attr('class', 'county')
                .attr('d', path)
                .attr('fill', d => colorScale(populationById[d.id]));

            svg.append('path')
                .datum(topojson.mesh(us, us.objects.states, (a, b) => a !== b))
                .attr('class', 'states')
                .attr('d', path);

            // Add legend
            let legend = svg.selectAll('.legend')
                .data(colorScale.range().map(d => {
                    let r = colorScale.invertExtent(d);
                    if (!r[0]) r[0] = colorScale.domain()[0];
                    if (!r[1]) r[1] = colorScale.domain()[1];
                    return r;
                }))
                .enter().append('g')
                .attr('class', 'legend');

            legend.append('rect')
                .attr('x', (d, i) => 20 + i * 40)
                .attr('y', height - 40)
                .attr('width', 40)
                .attr('height', 20)
                .attr('fill', d => colorScale(d[0]));

            legend.append('text')
                .attr('class', 'legend')
                .attr('x', (d, i) => 20 + i * 40)
                .attr('y', height - 45)
                .attr('dy', '0.35em')
                .attr('fill', '#000')
                .text(d => Math.round(d[0]));
        }).catch(error => {
            console.error('Error loading data:', error);
        });
    </script>
</body>
</html>
```

**Explanation**:
- SVG container is created for the map.
- GeoJSON data and CSV population data are loaded and processed.
- Color scale is defined for the population data.
- Counties are colored based on population data using the color scale.
- A legend is added to indicate the population ranges.

### Conclusion

By understanding and using D3.js for creating advanced visualizations such as network graphs, heatmaps, and geospatial visualizations, you can build sophisticated and interactive data visualizations that provide valuable insights. Practice these concepts to build a strong foundation in advanced D3.js techniques.

### Further Reading
- [D3.js Official Documentation](https://d3js.org/)
- [D3.js Force Layout Documentation](https://github.com/d3/d3-force)
- [D3.js GeoPath Documentation](https://github.com/d3/d3-geo#path)
- [D3.js Scale Documentation](https://github.com/d3/d3-scale)
- [TopoJSON Documentation](https://github.com/topojson/topojson)
- [Interactive Data Visualization for the Web by Scott Murray](http://shop.oreilly.com/product/0636920037318.do)