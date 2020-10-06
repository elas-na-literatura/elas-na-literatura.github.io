---
layout: default
title: Autoras
permalink: /autoras/
---

<h1>Autoras</h1>
<p>Confira abaixo uma linha do tempo explicativa que abrange as autoras contempladas neste site inseridas em seu tempo histórico, baseado em seu ano de nascimento!</p>

<div class="line" id="timeline">
    <span class="dot" onclick="slide('1882')">1822</span>
    <span class="infobox" id="1882"><h1>Hello, World!</h1>Teste 1</span><br>

    <span class="dot" onclick="slide('1921')">1921</span>
    <span class="infobox" id="1921"><h1>Hello, World!</h1>Teste 2</span><br>

    <span class="dot" onclick="slide('2020')">2020</span>
    <span class="infobox" id="2020"><h1>Hello, World!</h1>Teste 3</span><br>
</div>

<br><br>

<script>
    let timeline = document.getElementById('timeline');
    let timelineState = "center";
    let lastButton = "";

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

            lastButton = "";
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

            if(lastButton != "" && lastButton != last)
            {
                var lastInfobox = document.getElementById(lastButton);
                lastInfobox.style.animationName = 'hide';
                lastInfobox.style.animationDuration = '0.5s';
                lastInfobox.style.opacity = '0';
            }                  
                    
            lastButton = last;
        }
    }
</script>