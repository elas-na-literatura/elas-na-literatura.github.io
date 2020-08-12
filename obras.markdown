---
layout: page
title: Obras
permalink: /obras/
onLoadFunction: autora()
livros: [
["A viúva Simões", "Júlia Lopes de Almeida", "1897", "Realismo", "https://images-na.ssl-images-amazon.com/images/I/41LokrPE6jL._SX311_BO1,204,203,200_.jpg"],
["A Intrusa", "Júlia Lopes de Almeida", "1908", "Realismo", "https://m.media-amazon.com/images/I/51T2IipVdtL.jpg"]
]
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
	obrasMesmo = [];
	var autoraBar = document.getElementById("autorabox");
	var autoraVal = autoraBar.value;
    	for(i in obras)
    	{
		var novaAutora = string_to_slug_mod(obras[i].autora);
    		if(novaAutora.includes(string_to_slug_mod(autoraVal)))
        	{
        		obrasMesmo[obrasMesmo.length] = obras[i];
        	}
    	}
	search();
}

function search()
{
	obrasDeVerdade = [];
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
  	if(escola != "Todas" && obrasDeVerdade[i].escola != escola) continue;
    document.getElementById("demo").innerHTML += 
    '<div class="bookpreview">\n'+
	'<div class="row">\n'+
    '<div class="columncapatwo">\n<img src=' + obrasDeVerdade[i].imagem + '>\n</div>\n'+
    '<div class="columntwo">\n'+
    '<tag style="font-weight:900;font-size:36px">' + obrasDeVerdade[i].titulo + '</tag>\n<br>\n' +
    '<tag style="color:#505050;font-size:25px"><i><b>' + obrasDeVerdade[i].autora + '</b> - ' + obrasDeVerdade[i].ano + '</i></tag>\n<br><br>\n' +
    '<button class="button" onclick=\'window.open("{{ site.url }}obras/' + obrasDeVerdade[i].link + '", "_self")\'>Conferir Obra</button>\n'+
    '</div>\n</div>\n</div>\n<br>\n';
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
<select id="filtros" onload="escolaLit()" onchange="autora()">
  <option>Todas</option>
  <option>Realismo</option>
  <option>Parnasianismo</option>
  <option>Pré-Modernismo</option>
</select> <br>
Autora: 🔍
<input type="text" id="autorabox" value="" oninput="autora()"><br>
Nome da Obra: 🔍
<input type="text" id="termo" value="" oninput="autora()"><br>
</form>
<p id="demo"></p>
