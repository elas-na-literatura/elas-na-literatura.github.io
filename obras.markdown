---
layout: page
title: Obras
permalink: /obras/
onLoadFunction: processURLParams()
---
<script>
var share = true;

var obras = [];
{% for pagina in site.pages %}
{% if pagina.dir == "/obras/"%}
{% if pagina.name != "obras.markdown"%}
obras[obras.length] = {titulo:"{{ pagina.nomelivro }}", autora:"{{ pagina.nomeautora }}", ano:"{{ pagina.anolancamento }}", escola:"{{ pagina.layout }}", imagem:"{{ pagina.imagemcapa }}", link:"{{ pagina.nomelivro | slugify: "latin"}}", dest:"{{ pagina.link || default: 'https://www.youtube.com/watch?v=dQw4w9WgXcQ' }}", destname:"{{ pagina.fontelivro | default: "YouTube" }}", quote:"{{ pagina.quote | strip_newlines }}", quotepag:"{{ pagina.quotepagina }}"};
{% endif %}
{% endif %}
{% endfor %}

var obrasMesmo = [];
var obrasDeVerdade = [];

var obrasPorPagina = 10, atualPagina = 1, pagMax = 1;

// Processamento de parâmetros no URL
function processURLParams()
{
  var url = window.location.href;
  if(url.includes("?"))
  {
    var params = url.substring(url.indexOf("?")+1).split("&");
    for(i in params)
    {
      setParam(params[i]);
    }
  }
  processParams();
}

// Método para mudar valores do HTML baseado no URL
function setParam(param)
{
  var values = param.split("=")
  if(values.length = 2)
  {
    try
    {
      document.getElementById(values[0]).value = values[1].replace(/\+/g, " ").replace(/(%20)/g, " "); 
    }
    catch(err)
    {
      
    }
  }
}

// Processamento do número de páginas
function processParams()
{
  obrasPorPagina = parseInt(document.getElementById("opp").options[document.getElementById("opp").selectedIndex].text);
  if(!Number.isInteger(obrasPorPagina))
  {
    obrasPorPagina = 99999;
  }
  atualPagina = parseInt(document.getElementById("paginaatual").value)
  if(document.getElementById("paginaatual").value == "" || atualPagina < 1) atualPagina = 1;
  autora();
}

// Filtro por nome de autora
function autora()
{
	obrasMesmo = [];
	var autoraBar = document.getElementById("nomeautora");
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

// Filtro por nome de obra
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

// Filtro por tipo de texto (previamente de escola literária) + Paginação
function escolaLit() {
  var escolaOptions = document.getElementById("filtros");
  var escola = escolaOptions.options[escolaOptions.selectedIndex].text;
  document.getElementById("demo").innerHTML = "";
  
  // Paginação
  pagMax = Math.ceil(obrasDeVerdade.length / obrasPorPagina);
  if(atualPagina > pagMax) atualPagina = pagMax
  document.getElementById("paginaatual").value = atualPagina;
  var obraOffset = (obrasPorPagina * (atualPagina - 1))
  var obraEmPag = 0;

  // Adição de obras no HTML
  for(val in obrasDeVerdade)
  {
    var i = parseInt(val) + obraOffset;
    if(obraEmPag >= obrasPorPagina) continue;
    if(escola != "Todas" && obrasDeVerdade[i].escola != escola.toLowerCase()) continue;
    switch(obrasDeVerdade[i].escola)
    {
      case "prosa":
        document.getElementById("demo").innerHTML += 
        '<div class="bookpreview">\n'+
        '<div class="row">\n'+
        '<div class="columncapatwo">\n<img src=' + obrasDeVerdade[i].imagem + '>\n</div>\n'+
        '<div class="columntwo">\n'+
        '<tag style="font-weight:900;font-size:36px">' + obrasDeVerdade[i].titulo + '</tag>\n<br>\n' +
        '<tag style="color:#505050;font-size:25px"><i><b>' + obrasDeVerdade[i].autora + '</b> - ' + obrasDeVerdade[i].ano + '</i></tag>\n<br><br>\n' +
        '<button class="button" onclick=\'window.open("{{ site.url }}obras/' + obrasDeVerdade[i].link + '", "_self")\'>Conferir Obra</button><br><br>\n'+
        '<a href="https://api.whatsapp.com/send?text=Olha%20essa%20obra%20maravilhosa%20da%20' + encodeURI(obrasDeVerdade[i].autora) + '%20que%20eu%20encontrei%21%0A' + encodeURI("{{ site.url }}obras/" + obrasDeVerdade[i].link) + '" target="_blank"><img src="https://elas-na-literatura.github.io/rsc/whatsapp.svg" alt="WhatsApp"></a>'+
        '<a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-text="Olha essa obra maravilhosa da ' + obrasDeVerdade[i].autora + ' que eu encontrei! " data-url="https://elas-na-literatura.github.io/obras/' + obrasDeVerdade[i].link + '" data-hashtags="ElasNaLiteratura" data-lang="pt" data-show-count="false">Tweet</a>'+
        '<iframe src="https://www.facebook.com/plugins/share_button.php?href=' + encodeURI("{{ site.url }}obras/" + obrasDeVerdade[i].link) + '&layout=button&size=small&width=110&height=20&appId" width="110" height="20" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowTransparency="true" allow="encrypted-media"></iframe>\n'+
        '</div>\n</div>\n</div>\n<br>\n';
        break;
      case "poesia":
        document.getElementById("demo").innerHTML += 
        '<div class="bookpreview">\n'+
        '<tag style="font-weight:900;font-size:36px">' + obrasDeVerdade[i].titulo + '</tag>\n<br>\n' +
        '<tag style="color:#505050;font-size:25px"><i><b>' + obrasDeVerdade[i].autora + '</b> - ' + obrasDeVerdade[i].ano + '</i></tag>\n<br>\n' +
        '<div class="quote" style="font-weight:400">\n<i>\n<tag style="font-size: 200%">&#x201c</tag><br>\n' +
        '<div class="center">' + obrasDeVerdade[i].quote + '</div><br>\n<div style="font-size: 200%" class="right"> &#x201d <br>\n' +
        '<p style="font-size: 50%"><tag style="font-weight:750">' + obrasDeVerdade[i].titulo + '</tag>, ' + obrasDeVerdade[i].quotepag + 'ª Estrofe.</p></div></i></div>' +
        '<button class="button" onclick=\'window.open("' + obrasDeVerdade[i].dest + '", "_self")\'>Acesse via ' + obrasDeVerdade[i].destname + '!</button>\n'+
        '\n</div>\n<br>\n';
        break;
    }
    obraEmPag++;
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
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
<form>
Obras por página:
<select id="opp" onchange="processParams()">
  <option>5</option>
  <option>10</option>
  <option>25</option>
  <option>50</option>
  <option>100</option>
  <option>Todas</option>
  <!-- <option>Pré-Modernismo</option> -->
  <!-- <option>Modernismo</option> -->
  <!-- <option></option> -->
</select> <br>
Tipo de Obra Literária:
<select id="filtros" onload="escolaLit()" onchange="autora()">
  <option>Todas</option>
  <option>Prosa</option>
  <option>Poesia</option>
  <!-- <option>Pré-Modernismo</option> -->
  <!-- <option>Modernismo</option> -->
  <!-- <option></option> -->
</select> <br>
Autora: 🔍
<input type="text" id="nomeautora" value="" oninput="autora()"><br>
Nome da Obra: 🔍
<input type="text" id="termo" value="" oninput="autora()"><br>
</form>
<p id="demo"></p>
<div style="position: fixed;width: 600px;bottom: 15px;margin: auto;/* min-width: 300px; */border-radius: 5px;background: #F0F0F0;border: 2px solid #CDCDCD;box-shadow: 0px 5px 10px #AAAAAA;z-index: 50;padding: 5px 5px;align-content: center;">
<form>
Página Atual
<input type="number" id="paginaatual" value="1" oninput="processParams()"><br>
</form>
</div>