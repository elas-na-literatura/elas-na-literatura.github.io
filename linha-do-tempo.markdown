---
layout: default
---

<h1>Linha do Tempo:</h1>
<p>Clique em um trecho da linha do tempo para saber mais sobre a escola literária deste período de tempo!</p>
<img id="ldt" src="../rsc/ldt/ldt.png" alt="Linha do Tempo" usemap="#ldtmap" width="680px">
<map id="ldtmapid" name="ldtmap">
    <area shape="rect" coords="3,2,170,53" alt="Realismo" onclick="changeDescription()">
    <!-- <area shape="rect" coords="806,9,1597,257" alt="Simbolismo" onclick="changeDescription('Simbolismo')"> -->
</map>

<script>
function changeDescription()
{
    alert('Description changed.');
    /* switch(escola)
    {
        case "Realismo":
            document.getElementByID("title").innerText = "Realismo";
            document.getElementByID("desc").innerText = "O Realismo é definido por lorem ipsum dolor sit amet.";
            break;

        case "Simbolismo":
            document.getElementByID("title").innerText = "Simbolismo";
            document.getElementByID("desc").innerText = "O Simbolismo é definido por lorem ipsum dolor sit amet.";
            break;
    } */
}
</script>

<h2 id=title style="color:#57ABEC"></h2>
<p id = desc></p>