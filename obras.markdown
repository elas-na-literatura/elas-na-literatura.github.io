---
layout: page
title: Obras
permalink: /obras/
onLoadFunction: search()
livros: [["A viúva Simões", "Júlia Lopes de Almeida", "1897", "Realismo", "https://images-na.ssl-images-amazon.com/images/I/41LokrPE6jL._SX311_BO1,204,203,200_.jpg"],
["exemplo", "Adélia Prado", "2020", "Parnasianismo", "https://www.escritas.org/autores/adelia-prado.jpg"],
["teste", "dfsfdsfsd", "3132", "Pré-Modernismo", ""]]
---
<script>
var obras = [];
{% for livro in page.livros %}
obras[{{ forloop.index0 }}] = {titulo:"{{ livro[0] }}", autora:"{{ livro[1] }}", ano:"{{ livro[2] }}", escola:"{{ livro[3] }}", imagem:"{{ livro[4] }}", link:"{{ livro[0] | slugify: "latin"}}"};
{% endfor %}

var obrasMesmo = [];
var obrasDeVerdade = [];

function autora()
{
	obrasMesmo = []
	var searchBar = document.getElementById("autora");
	var autora = searchBar.value;
    	for(i in obras)
    	{
		var novaAutora = string_to_slug_mod(obras[i].autora);
    		if(novaAutora.includes(string_to_slug_mod(autora)))
        	{
        		obrasMesmo[obrasMesmo.length] = obras[i];
        	}
    	}
	search();
}

function search()
{
	obrasDeVerdade = []
	var searchBar = document.getElementById("termo");
	var termo = searchBar.value;
    	for(i in obrasMesmo)
    	{
		var novoTitulo = string_to_slug_mod(obrasMesmo[i].titulo);
    		if(novoTitulo.includes(string_to_slug_mod(termo)))
        	{
        		obrasDeVerdade[obrasDeVerdade.length] = obrasMesmo[i];
        	}
    	}
	escolaLit();
}

function escolaLit() {
  var escolaOptions = document.getElementById("filtros");
  var escola = escolaOptions.options[escolaOptions.selectedIndex].text;
  document.getElementById("demo").innerHTML = "";
  
  for (i in obrasDeVerdade)
  {
  	if(escola != "--" && obrasDeVerdade[i].escola != escola) continue;
    document.getElementById("demo").innerHTML += 
    '<div class="bookpreview">'+
	'<div class="row">'+
    '<div class="columncapatwo"><img src=' + obrasDeVerdade[i].imagem + '> </div>'+
    '<div class="columntwo">'+
    '<b style="font-weight:900;font-size:25px">' + obrasDeVerdade[i].titulo + '</b><br>' +
    '<tag style="color:#505050;font-size:16px"><i><b>' + obrasDeVerdade[i].autora + '</b> - ' + obrasDeVerdade[i].ano + '</i></tag><br><br>' +
    '<button class="button" onclick=\'window.open("{{ site.url }}obras/' + obrasDeVerdade[i].link + '", "_blank")\'>Conferir Obra</button>'+
    '</div></div></div>';
  }
}

function string_to_slug_mod (str) {
    str = str.replace(/^\s+|\s+$/g, ''); // trim
    str = str.toLowerCase();
    // remove accents, swap ñ for n, etc
    var from = "ãàáäâèéëêìíïîòóöôùúüûñç·/_,:;õ";
    var to   = "aaaaaeeeeiiiioooouuuunc      o";
    for (var i=0, l=from.length ; i<l ; i++) {
        str = str.replace(new RegExp(from.charAt(i), 'g'), to.charAt(i));
    }
    str = str.replace(/[^a-z0-9 -]/g, '') // remove invalid chars
        .replace(/\s+/g, ' ') // collapse whitespace and replace by spacebar
        .replace(/ +/g, ' '); // collapse spaces
	return str;
}
</script>
<form>
Escola Literária:
<select id="filtros" onload="escolaLit()" onchange="search()">
  <option>--</option>
  <option>Realismo</option>
  <option>Parnasianismo</option>
  <option>Pré-Modernismo</option>
</select>
Autora:
<input type="text" id="autora" value="" oninput="search()"><br>
Nome da Obra:
<input type="text" id="termo" value="" oninput="search()"><br>
</form>
<p id="demo"></p>
