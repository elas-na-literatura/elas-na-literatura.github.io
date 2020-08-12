---
layout: page
title: Obras
permalink: /obras/
livros: [["A viúva Simões", "Júlia Lopes de Almeida", "1897", "Realismo", "https://images-na.ssl-images-amazon.com/images/I/41LokrPE6jL._SX311_BO1,204,203,200_.jpg"],
["exemplo", "Adélia Prado", "2020", "Parnasianismo", "https://www.escritas.org/autores/adelia-prado.jpg"],
[""]]
---

Está página está em desenvolvimento.

<script>
var obras = [];
{% for livro in page.livros %}
obras[{{ forloop.index0 }}] = {titulo:"{{ livro[0] }}", autora:"{{ livro[1] }}", ano:"{{ livro[2] }}", escola:"{{ livro[3] }}", imagem:"{{ livro[4] }}", link:"{{ livro[0] | slugify: "latin"}}"};
{% endfor %}

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
    '<div class="columncapatwo"><img src=' + obras[i].imagem + '> </div>'+
    '<div class="columntwo">'+
    '<b style="font-weight:900;font-size:25px">' + obras[i].titulo + '</b><br>' +
    '<tag style="color:#505050;font-size:16px"><i><b>' + obras[i].autora + '</b> - ' + obras[i].ano + '</i></tag><br><br><br>' +
    '<button class="button" onclick=\'window.open("{{ site.url }}obras/' + obras[i].link + '", "_blank")\'>Conferir Obra</button>'+
    '</div></div></div>';
    // obras[i].titulo + ", de " + obras[i].autora + ".<br>";
  }
}
</script>
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
