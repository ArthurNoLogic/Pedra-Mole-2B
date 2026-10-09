<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arthur - Perfil</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <button id="botaoTema">🌙 Modo Escuro</button>

    <main class="foto">
        <h1>Arthur</h1>
        <img src="https://i.pinimg.com/736x/ab/d3/16/abd316d3f67c507b1416036c41069574.jpg" alt="foto de perfil">
        <p>estudante de analise e desenvolvimento de sistemas</p>
        <p>bio</p>
        <a href="#">contato</a>
    </main>

    <script>
        const botaoTema = document.getElementById('botaoTema');
        const temaSalvo = localStorage.getItem('tema');
        if (temaSalvo === 'dark') {
            document.body.classList.add('dark-mode');
            if (botaoTema) botaoTema.textContent = '☀️ Modo Claro';
        }

        if (botaoTema) {
            botaoTema.addEventListener('click', () => {
                document.body.classList.toggle('dark-mode');
                
                if (document.body.classList.contains('dark-mode')) {
                    botaoTema.textContent = '☀️ Modo Claro';
                    localStorage.setItem('tema', 'dark');
                } else {
                    botaoTema.textContent = '🌙 Modo Escuro';
                    localStorage.setItem('tema', 'light');
                }
            });
        }
        const paragrafoBio = document.querySelector('.foto p'); 
        if (paragrafoBio) {
            const textoOriginal = paragrafoBio.textContent;
            paragrafoBio.textContent = ''; 
            let i = 0;

            function digitar() {
                if (i < textoOriginal.length) {
                    paragrafoBio.textContent += textoOriginal.charAt(i);
                    i++;
                    setTimeout(digitar, 40); 
                }
            }
            setTimeout(digitar, 500);
        }

        const linkContato = document.querySelector('.foto a');
        if (linkContato) {
            linkContato.addEventListener('click', (evento) => {
                evento.preventDefault(); 
                linkContato.style.transform = 'scale(0.95)';
                setTimeout(() => {
                    linkContato.style.transform = 'scale(1)';
                }, 150);

                alert('Redirecionando para as opções de contato do Arthur!');
            });
        }
    </script>
</body>
</html>
