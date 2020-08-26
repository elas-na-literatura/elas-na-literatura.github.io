---
layout: default
---

<h1>Linha do Tempo:</h1>
<p>Clique em um trecho da linha do tempo para saber mais sobre a escola literária deste período de tempo!</p>
<img id="ldt" src="../rsc/ldt/ldt.png" alt="Linha do Tempo" usemap="#ldtmap" width="680px">
<map id="ldtmapid" name="ldtmap">
    <area shape="rect" coords="3,2,170,53" alt="Realismo" onclick="changeDescription('Realismo')">
    <!-- <area shape="rect" coords="806,9,1597,257" alt="Simbolismo" onclick="changeDescription('Simbolismo')"> -->
</map>

<script>
function changeDescription(escola)
{
    alert(`Description changed to ${escola}.`);
    switch(escola)
    {
        case 'Realismo':
            alert(`partiu realismo`);
            document.getElementByID("escTitle").innerHTML = "Realismo";
            document.getElementByID("escDesc").innerHTML = "O Realismo é definido por lorem ipsum dolor sit amet.";
            break;

        case 'Simbolismo':
            document.getElementByID("escTitle").innerHTML = "Simbolismo";
            document.getElementByID("escDesc").innerHTML = "O Simbolismo é definido por lorem ipsum dolor sit amet.";
            break;
    }
}
</script>

<h2 id=escTitle style="color:#57ABEC"></h2>
<p id=escDesc></p>