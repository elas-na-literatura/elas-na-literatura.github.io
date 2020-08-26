---
layout: default
---

<h1>Linha do Tempo:</h1>

<img scr="rsc/ldt/ldt.png" alt="Linha do Tempo" usemap="#ldtmap" width="100%" id="ldt">
<map id="ldtmapid" name="ldtmap">
    <area shape="rect" coords="15,9,806,257" alt="Realismo" onclick="changeDescription('Realismo')">
    <area shape="rect" coords="806,9,1597,257" alt="Simbolismo" onclick="changeDescription('Simbolismo')">
</map>

<script>
function changeDescription(escola)
{
    switch(escola)
    {
        case "Realismo":
            document.getElementByID("title").innerText = "Realismo";
            document.getElementByID("desc").innerText = "O Realismo é definido por lorem ipsum dolor sit amet.";
            break;

        case "Simbolismo":
            document.getElementByID("title").innerText = "Simbolismo";
            document.getElementByID("desc").innerText = "O Simbolismo é definido por lorem ipsum dolor sit amet.";
            break;
    }
}

window.onload = function () {
    var ImageMap = function (map, img) {
            var n,
                areas = map.getElementsByTagName('area'),
                len = areas.length,
                coords = [],
                previousWidth = 128;
            for (n = 0; n < len; n++) {
                coords[n] = areas[n].coords.split(',');
            }
            this.resize = function () {
                var n, m, clen,
                    x = img.offsetWidth / previousWidth;
                for (n = 0; n < len; n++) {
                    clen = coords[n].length;
                    for (m = 0; m < clen; m++) {
                        coords[n][m] *= x;
                    }
                    areas[n].coords = coords[n].join(',');
                }
                previousWidth = document.body.clientWidth;
                return true;
            };
            window.onresize = this.resize;
        },
        imageMap = new ImageMap(document.getElementById('ldtmapid'), document.getElementById('ldt'));
    imageMap.resize();
    return;
}
</script>

<h2 id=title style="color:#57ABEC"></h2>
<p id = desc></p>