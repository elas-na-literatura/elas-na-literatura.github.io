---
layout: default
---

<h1>Linha do Tempo:</h1>
<p>Clique em um trecho da linha do tempo para saber mais sobre a escola literária deste período de tempo, além de obras importantes do período!</p>
<img id="ldt" src="../rsc/ldt/ldt.svg" alt="Linha do Tempo" usemap="#ldtmap" width="680px">
<map id="ldtmapid" name="ldtmap">
    <area shape="rect" coords="93,0,258,57" alt="Realismo" onclick="changeDescription('Realismo')">
    <area shape="rect" coords="258,0,423,57" alt="Simbolismo" onclick="changeDescription('Simbolismo')">
    <area shape="rect" coords="423,0,588,57" alt="Pré-Modernismo" onclick="changeDescription('Pré-Modernismo')">
    <area shape="rect" coords="588,0,680,57" alt="Modernismo" onclick="changeDescription('Modernismo')">
    <!-- <area shape="rect" coords="806,9,1597,257" alt="Simbolismo" onclick="changeDescription('Simbolismo')"> -->
</map>

<h1 id=escTitle style="font-size:350%; color:#57ABEC" class="escTitulo"></h1>
<p id=escDesc></p>

<script>
function changeDescription(escola)
{
    switch(escola)
    {
        case 'Realismo':
            document.getElementById('escTitle').innerHTML = '<b>Realismo</b>';
            document.getElementById('escTitle').style.color = '#ffa781';
            document.getElementById('escDesc').innerHTML = 'O Realismo é definido por lorem ipsum dolor sit amet.';
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
</script>