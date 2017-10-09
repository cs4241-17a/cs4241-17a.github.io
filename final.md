---
layout: page
title: final
---

Details:<br>
October 12<br>
Riley Hall<br>
12p - 2p

Food Types:<br>
Coffee<br>
Breakfast sandwiches<br>
Assorted pastries<br>

## fundraising

Note: we are shooting for $750<br>
Food cost per student is ~$10.<br>
Typical contributions range from $5-$20.<br>

(24-Sep-2017 as shown in the graph below, I've kicked us off with $100.)

- [venmo @laneharrison](https://venmo.com/laneharrison)
- [square cash @laneharrison](https://cash.me/$laneharrison)

<svg id="fuv" width="768" height="500"></svg>

## poll on whether we do catering or not

[![](https://m131jyck4m.execute-api.us-west-2.amazonaws.com/prod/poll/01BS93EVTQQHJ0MH9MCFM9BB4G/Yes%3A%20food%20please%20and%20I%20can%20contribute%20%24)](https://m131jyck4m.execute-api.us-west-2.amazonaws.com/prod/poll/01BS93EVTQQHJ0MH9MCFM9BB4G/Yes%3A%20food%20please%20and%20I%20can%20contribute%20%24/vote)
[![](https://m131jyck4m.execute-api.us-west-2.amazonaws.com/prod/poll/01BS93EVTQQHJ0MH9MCFM9BB4G/No%3A%20food%20not%20necessary)](https://m131jyck4m.execute-api.us-west-2.amazonaws.com/prod/poll/01BS93EVTQQHJ0MH9MCFM9BB4G/No%3A%20food%20not%20necessary/vote)

<script>
var svg = d3.select("#fuv"),
    margin = {top: 20, right: 20, bottom: 30, left: 50},
    width = +svg.attr("width") - margin.left - margin.right,
    height = +svg.attr("height") - margin.top - margin.bottom,
    g = svg.append("g").attr("transform", "translate(" + margin.left + "," + margin.top + ")");

var parseTime = d3.timeParse("%d-%b-%y");

var x = d3.scaleTime()
    .rangeRound([0, width]);

var y = d3.scaleLinear()
    .rangeRound([height, 0]);

var line = d3.line()
    .x(function(d) { return x(d.date); })
    .y(function(d) { return y(d.close); });

d3.tsv("funds.tsv", function(d) {
  d.date = parseTime(d.date);
  d.close = +d.close;
  return d;
}, function(error, data) {
  if (error) throw error;

//  x.domain(d3.extent(data, function(d) { return d.date; }));
  x.domain([parseTime('24-Sep-17'), parseTime('10-Oct-17')]);
//  y.domain(d3.extent(data, function(d) { return d.close; }));
  y.domain([0, 750]);

  g.append("g")
      .attr("transform", "translate(0," + height + ")")
      .call(d3.axisBottom(x))
    .select(".domain")
      .remove();

  g.append("g")
      .call(d3.axisLeft(y))
    .append("text")
      .attr("fill", "#000")
      .attr("transform", "rotate(-90)")
      .attr("y", 6)
      .attr("dy", "0.71em")
      .attr("text-anchor", "end")
      .text("Price ($)");

  g.append("path")
      .datum(data)
      .attr("fill", "none")
      .attr("stroke", "steelblue")
      .attr("stroke-linejoin", "round")
      .attr("stroke-linecap", "round")
      .attr("stroke-width", 1.5)
      .attr("d", line);
});
</script>
