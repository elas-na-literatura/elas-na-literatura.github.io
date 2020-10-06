---
layout: default
title: Linha do Tempo
permalink: /linha-do-tempo/
---

<h1>Linha do Tempo:</h1>
<p>Confira abaixo uma linha do tempo explicativa que abrange as autoras contempladas neste site inseridas em seu tempo histórico-literário!</p>
<p>Clique em um trecho da linha do tempo para saber mais sobre a escola literária deste período de tempo, além do que foi explicado acima!</p>

<!-- <img id="ldt" src="../rsc/ldt/ldt.svg" alt="Linha do Tempo" usemap="#ldtmap" width="680px" style="min-width:680px">
<map id="ldtmapid" name="ldtmap">
    <area shape="rect" coords="64,0,120,57" alt="1862" onclick="changeDescription('1862')">
    <area shape="rect" coords="258,0,423,57" alt="Simbolismo" onclick="changeDescription('Simbolismo')">
    <area shape="rect" coords="423,0,588,57" alt="Pré-Modernismo" onclick="changeDescription('Pré-Modernismo')">
    <area shape="rect" coords="588,0,680,57" alt="Modernismo" onclick="changeDescription('Modernismo')">
    <area shape="rect" coords="806,9,1597,257" alt="Simbolismo" onclick="changeDescription('Simbolismo')">
</map> -->

<!-- <h1 id=escTitle style="font-size:350%; color:#57ABEC" class="escTitulo"></h1>
<h1 id=escAutora style="font-size:200%"></h1>
<p id=escDesc></p>  -->

<div class="line" id="timeline">
    <span class="dot" onclick="slide('1882')">1822</span>
    <span class="infobox" id="1882"><h1>Hello, World!</h1>Test?</span><br>

    <span class="dot" onclick="slide('1921')">1921</span>
    <span class="infobox" id="1921"><h1>Hello, World!</h1>Test?</span><br>

    <span class="dot" onclick="slide('2020')">2020</span>
    <span class="infobox" id="2020"><h1>Hello, World!</h1>Test?</span><br>
</div>

<script>

            let timeline = document.getElementById('timeline');
            let timelineState = "center";
            let lastButton = "";
            let openBox = ""

            function slide(last)
            {
                if(lastButton == last )
                {
                    timeline.style.left = '50%'; 
                    timeline.style.animationName = 'slideRight'; 
                    timeline.style.animationDuration = '1s';
                    timelineState = "center";

                    var infobox = document.getElementById(last);
                    infobox.style.animationName = 'hide';
                    infobox.style.animationDuration = '0.5s';
                    infobox.style.opacity = '0';

                    openBox = "";
                } 

                else
                {
                    timeline.style.left = '96px'; 
                    timeline.style.animationName = 'slideLeft'; 
                    timeline.style.animationDuration = '1s';
                    timelineState = "left";

                    var infobox = document.getElementById(last);
                    infobox.style.animationName = 'appear';
                    infobox.style.animationDuration = '0.5s';
                    infobox.style.opacity = '1';

                    if(openBox != "" && openBox != last)
                    {
                        var lastInfobox = document.getElementById(openBox);
                        lastInfobox.style.animationName = 'hide';
                        lastInfobox.style.animationDuration = '0.5s';
                        lastInfobox.style.opacity = '0';
                    }                  
                            
                    openBox = last;
                }

                lastButton = last;
            }

/*
function changeDescription(ano)
{
    switch(ano)
    {
        case '1862':
            document.getElementById('escTitle').innerHTML = '<b>1862</b>';
            document.getElementById('escTitle').style.color = '#ffa781';
            document.getElementById('escAutora').innerHTML = '<b>Júlia Lopes de Almeida</b>';
            document.getElementById('escDesc').innerHTML = 'Júlia Lopes de Almeida foi uma escritora abolicionista carioca, defensora da educação feminina, que nasceu em 24 de Setembro de 1862 e morreu em 30 de Maio de 1934. Foi autora de diversas obras, e uma das primeiras mulheres brasileiras a receber aclamação por suas obras, e foi uma das idealizadoras da Academia Brasileira de Letras. Foi mãe também da fundadora da nova escola brasileira de declamação, Margarida Lopes de Almeida.';
            document.getElementById('escDesc').innerHTML += '<br><br><button class="button" onclick=\'window.open("{{ site.url }}obras/?nomeautora=Julia+Lopes+de+Almeida", "_self")\'>Acesse Aqui Suas Obras</button>';
            break;

        case 'Simbolismo':
            document.getElementById('escTitle').innerHTML = '<b>Simbolismo</b>';
            document.getElementById('escTitle').style.color = '#fff981';
            document.getElementById('escDesc').innerHTML = 'O Simbolismo é definido por lorem ipsum dolor sit amet.';
            break;

        case 'Pré-Modernismo':
            document.getElementById('escTitle').innerHTML = '<b>Pré-Modernismo</b>';
            document.getElementById('escTitle').style.color = '#a4ff81';
            document.getElementById('escDesc').innerHTML = 'O Pré-Modernismo é definido por lorem ipsum dolor sit amet.';
            break;

        case 'Modernismo':
            document.getElementById('escTitle').innerHTML = '<b>Modernismo</b>';
            document.getElementById('escTitle').style.color = '#81ddff';
            document.getElementById('escDesc').innerHTML = 'O Modernismo é definido por lorem ipsum dolor sit amet.';
            break;
    }
}
*/
</script> -->