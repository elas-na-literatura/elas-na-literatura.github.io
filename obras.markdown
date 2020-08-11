---
layout: page
title: Obras
permalink: /obras/
---

Está página está em desenvolvimento.

<script>
var obras = [];
obras[0] = {titulo:"abcde", ano:1879, autora:"linda", escola:"Realismo"};
obras[1] = {titulo:"gfsdgfds", ano:1902, autora:"ana", escola:"Parnasianismo"};
obras[2] = {titulo:"dfdavc", ano:1899, autora:"martha", escola:"Realismo"};
obras[3] = {titulo:"fdvrgf", ano:1876, autora:"claudia", escola:"Realismo"};
obras[4] = {titulo:"fdsavre", ano:1879, autora:"janaina", escola:"Pré-Modernismo"};
obras[5] = {titulo:"htwfg", ano:1900, autora:"claudia", escola:"Realismo"};

function escolaLit() {
  var escolaOptions = document.getElementById("filtros");
  var escola = escolaOptions.options[escolaOptions.selectedIndex].text;
  document.getElementById("demo").innerHTML = "";
  
  for (i in obras)
  {
  	//document.getElementById("demo").innerHTML += "<br>" + obras[i].escola + " // " + escola;
  	if(escola != "--" && obras[i].escola != escola) continue;
    document.getElementById("demo").innerHTML += 
    '<div class="bookpreview">'+
	'<div class="row">'+
    '<div class="columncapatwo"><img src=https://images-na.ssl-images-amazon.com/images/I/31aX81I6vnL._SX351_BO1,204,203,200_.jpg> </div>'+
    '<div class="columntwo">'+
    '<h1 style="font-weight:900">' + obras[i].titulo + '</h1>' +
    '<h3 style="color:#505050"><i><b>' + obras[i].autora + '</b> - ' + obras[i].ano + '</i></h3>' +
    '<button>Confira Obra</button>'+
    '</div></div></div>';
    // obras[i].titulo + ", de " + obras[i].autora + ".<br>";
  }
}
</script>
</head>
<form>
Filtros:
<select id="filtros" onchange="escolaLit()">
  <option>--</option>
  <option>Realismo</option>
  <option>Parnasianismo</option>
  <option>Pré-Modernismo</option>
</select>
</form>
<p id="demo"></p>
