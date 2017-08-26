---
layout: page
title: fame
permalink: /fame/
---
Hall of Fame
---

<style>
.project {
  margin: 1em 0 0 0;
  padding: 0 0 0 1em;
}

.title {
    font-weight: bold;
    font-family: 'Changa', sans-serif;
    font-size: 24px;

}

.name {
    padding-left: 25px;
}

hr {
	height: 10px;
	border: 0;
	box-shadow: 0 10px 10px -10px #8c8b8b inset;
    padding-bottom: 20px;
}

iframe {
    padding-top: 15px;
}

</style>

<div id="fame" />

<script>

var fame_data = {{ site.data.fame | jsonify }};

var fame_div = d3.select('#fame');

fame_div.selectAll('.project')
  .data(fame_data)
  .enter().append('div')
  .attr('class', 'project')
  .html( render_project )

function render_project(d, i, A) {
    var s = '';
    s += '<link href="https://fonts.googleapis.com/css?family=Changa" rel="stylesheet">';
    s += '<hr>';

    s += '<div class="title">' + d.title.text + '</div>';
    s += '<div class="team">Team: ' + team_members(d.team) + '</div>';
    s += '<div class="description">Description: ' + d.description + '</div>';
    s += '<div class="repo">Github Repository: ' + '<a href="'+ d.repo +'">' + d.repo + '</a><div>';
    s += '<div class="link">Project Link: ' + '<a href="'+ d.link +'">' + d.link + '</a><div>';

    s += '<div class="frame"><iframe id="frame" src="'+ d.link +'" style="width:500px;" frameborder="0"></iframe></div>';

    s += '</br>';
    return s;
} 

function link_text(text, link) {
    var s = '';
    if (link != "") {
        s += '<a href ="' + link + '">' + text + '</a>';
    } else {
        s += text;
    }
    return s;
}

function team_members(d) {
    var s = '';
    d.forEach(function(person) {
        s += '<div class="name">' +link_text(person.name, person.site)+' ('+ person.email +')'+ '</div>'; 
    })
   
    return s;
}

</script>


