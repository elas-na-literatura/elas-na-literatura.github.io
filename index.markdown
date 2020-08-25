---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<section class="parallax">
            <img src="rsc/prlx/bgr.png" id=bgr>
            <img src="rsc/prlx/book.png" id=book>
            <h1 id=title>Bem vindo(a) ao nosso projeto!</h1>
        </section>
        <script type="text/javascript">
            let bgr = document.getElementById("bgr");
            let book = document.getElementById("book");
            let title = document.getElementById("title");

            window.addEventListener("scroll", function()
            {
                var scrollYValue = window.scrollY;

                bgr.style.top = -scrollYValue * 0.75 + 'px';
                book.style.top = -scrollYValue * 0.5 + 'px';
                title.style.top = -scrollYValue * 0.25 + 'px';
            });
        </script>

<p> Em aulas e livros de literatura brasileira, aprendemos sobre autores renomados como Machado de Assis, Guimarães Rosa, José de Alencar, Graciliano Ramos, entre outros. </p>
<h3>Suas obras são exemplares. Porém, onde se encontram as autoras de escolas literárias pré-modernistas?</h3>

<p>O nosso projeto visa, portanto, trazer à luz diversas obras de autoras brasileiras não representadas em aulas e livros.</p>

<h2>Que tal saber mais?</h2>
<button class="button" onclick='window.open("{{ site.url }}/obras","_self")'><b>Veja as obras do site!</b></button>
