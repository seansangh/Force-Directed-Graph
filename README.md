# Force-Directed-Graph

*D3 Force Graph*

This is an app that allows you to create a force-directed graph displaying national contiguity.



...

**Home Page**

<img src="/ForceDirectedGraph.PNG" title="home page" alt="home page" width="500px">


---


## Table of Contents 

> Sections
- [Sample Code](#Sample_Code)
- [Installation](#installation)
- [Features](#features)
- [Contributing](#contributing)
- [Team](#team)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)


---

## Sample Code

```javascript
// code

document.addEventListener('DOMContentLoaded', function(){
  req= new XMLHttpRequest();
  req.open('GET','https://raw.githubusercontent.com/DealPete/forceDirected/master/countries.json',true);
  req.send();
  req.onload=function(){
    data=JSON.parse(req.responseText);
    
  var w = 1000;
  var h = 800;
   
  var force = d3.layout.force()
     .charge(-100)
     .linkDistance(15)
     .size([w, h])
     .nodes(data.nodes)
     .links(data.links)
     .start();
  
  var svg = d3.select('#in')
      .append('svg')
      .attr("width", w)
      .attr("height", h);
    
    var img = d3.select("#in").selectAll(".img")
        .data(data.nodes)
        .enter()
        .append('section')
        .attr("class", "images")
        .html(function(f){
          return ("<img src='https://i.imgur.com/TiJ06ht.png' class='flag flag-"+f.code+"' />")
        })
        .attr("title", function(d){ return d.country; })
        .call(force.drag);
    
    var link = svg.selectAll(".link")
        .data(data.links)
        .enter()
        .append("line")
        .attr("class", "links")
   
    
    var node = svg.selectAll(".node")
        .data(data.nodes)
        .enter()
        .append("circle")
        .attr("class", "nodes")
        .attr("r", 1);   

    
    force.on("tick", function(){
      link.attr("x1", function(d){ return d.source.x; })
          .attr("y1", function(d){ return d.source.y; })
          .attr("x2", function(d){ return d.target.x; })
          .attr("y2", function(d){ return d.target.y; });

      
      img.attr("style", function(d){ 
       return ("top:"+(d.y - 10)+"px; left:"+(d.x - 10)+"px"); 
      });
      
      })   
    
    
  }
})
```

---

## Installation
## Features
## Usage (Optional)
## Documentation (Optional)
## Tests (Optional)
## Contributing
## Team

> Contributors/People

| [**seansangh**](https://github.com/seansangh) |
| :---: |
| [![seansangh](https://avatars0.githubusercontent.com/u/45724640?v=3&s=200)](https://github.com/seansangh)    |
| [`github.com/seansangh`](https://github.com/seansangh) | 

-  GitHub user profile

---

## FAQ

- **Have any *specific* questions?**
    - Use the information provided under *Support* for answers

---

## Support

Reach out to me at one of the following places!

- Twitter at [`@wwinvestingllc`](https://twitter.com/wwinvestingllc?lang=en)
- Github at [`seansangh`](https://github.com/seansangh)

---

## Donations (Optional)

- If you appreciate the code provided herein, feel free to donate to the author via [Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url).

[<img src="https://www.paypalobjects.com/webstatic/en_US/i/buttons/cc-badges-ppppcmcvdam.png" alt="Pay with PayPal, PayPal Credit or any major credit card" />](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url)

---

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
- Copyright 2019 © <a>S.S.</a>
