---
layout: default
title: Autoras
permalink: /autoras/
---

<h1>Autoras</h1>
<p>Confira abaixo uma linha do tempo explicativa que abrange as autoras contempladas neste site inseridas em seu tempo histórico, baseado em seu ano de nascimento!</p>

<div class="line" id="timeline">
    {% for pagina in site.pages %}
        {% if pagina.dir == "/autoras/" %}
            {% if pagina.name != "autoras.markdown" %}
                <span class="dot" onclick="slide('{{ pagina.nomeautora }}')">{{ pagina.anonascimento | replace: "b", "" }}</span>
                <span class="infobox" id="{{ pagina.nomeautora }}">
                    <div style="height: 196px; text-align: center;">
                        <img src="{{ pagina.fotoautora }}" style="height: 100%">
                    </div>
                    <div style="text-align: justify">
                        <h1>{{ pagina.nomeautora }}</h1>
                        <p>{{ pagina.biografia }}</p>
                    </div>
                    <br><br>
                    <button class="button" onclick='window.open("{{ site.url }}autoras/{{ pagina.nomeautora }}", "_blank")'><b>Veja suas obras!</b></button><br><br>{% capture encoded-link %}{{ pagina.anonascimento }} {{ pagina.nomeautora }}{% endcapture %}
                    <a href='https://api.whatsapp.com/send?text=Olha%20que%20autora%20maravilhosa%20que%20eu%20encontrei%3A%20{{ pagina.nomeautora | uri_escape }}%21%20%0Ahttps%3A%2F%2Felas-na-literatura.github.io%2Fautoras%2F{{ encoded-link | slugify }}' target="_blank"><img src="https://elas-na-literatura.github.io/rsc/whatsapp.svg" alt="WhatsApp"  style="margin-top:-12px;"></a>
                    <a href="https://twitter.com/share?ref_src=twsrc%5Etfw" class="twitter-share-button" data-text="Olha que autora maravilhosa que eu encontrei: {{ pagina.nomeautora }}! " data-url="https://elas-na-literatura.github.io/autora/{{ encoded-link }}" data-hashtags="ElasNaLiteratura" data-lang="pt" data-show-count="false"><img src="https://elas-na-literatura.github.io/rsc/twitter.svg" alt="Twitter"  style="margin-top:-12px;"></a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
                    <iframe src='https://www.facebook.com/plugins/share_button.php?href=https%3A%2F%2Felas-na-literatura.github.io%2Fautoras%2F{{ encoded-link | slugify }}&layout=button&size=small&width=110&height=20&appId' width="110" height="20" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowTransparency="true" allow="encrypted-media"></iframe>
                </span><br>
            {% endif %}
        {% endif %}
    {% endfor %}

    <span class="dot" onclick="slide('????')">????</span>
    <span class="infobox" id="????">As autoras <b>Isabel Lima</b>, <b>Luciana V. P. de Mendonça</b> e <b>Sylvia Senny</b> não se apresentam na linha do tempo tanto por não termos o acesso e quantidade de informações necessárias quanto por saber se as informações de fato diziam respeito à essas autoras. Contudo, ressaltamos que suas obras não são menos importantes e merecem serem lidas tanto quanto as outras se interessarem ao leitor. </span><br>
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
            infobox.style.zIndex = '-999999';

            lastButton = "";
        } 

        else
        {
            timeline.style.left = 'var(--openedPos)'; 
            timeline.style.animationName = 'slideLeft'; 
            timeline.style.animationDuration = '1s';
            timelineState = "left";

            var infobox = document.getElementById(last);
            infobox.style.animationName = 'appear';
            infobox.style.animationDuration = '0.5s';
            infobox.style.opacity = '1';
            infobox.style.zIndex = '100';

            if(lastButton != "" && lastButton != last)
            {
                var lastInfobox = document.getElementById(lastButton);
                lastInfobox.style.animationName = 'hide';
                lastInfobox.style.animationDuration = '0.5s';
                lastInfobox.style.opacity = '0';
                infobox.style.zIndex = '-999999';
            }                  
                    
            lastButton = last;
        }
    }
</script>