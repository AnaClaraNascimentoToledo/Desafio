# Desafio
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="shortcut icon" href="#">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.1/css/bulma.min.css">
    <link rel="stylesheet" href="desafio2.css">

    <title>Lenscope</title>
</head>
<body id="body">
    <nav class="navbar is-dark">
        <div class="navbar-brand">
          <a class="navbar-item" href="https://lenscope.com.br/" target="_blank">
            <img src="Documents/Minhas Imagens/lenscope.png"Lenscope" width="112" height="28">
          </a>
          <div class="navbar-menu">
            <div class="navbar-start">
                
                </a>
            </div>
        </div>
    </nav>
    <section class="section">
        <div class="hero is-small">
            <div class="hero-body">
                <form onsubmit="validate(event)">
                    <div class="container">
                        <div class="box">
                        <p class="title has-text-centered txt-block">Insira abaixo o seu grau esférico</p>

                        <div class="field is-horizontal is-grouped is-grouped-centered block centralize-lt">
                        <label class="label lb-mg">
                            Do olho esquerdo:
                        </label>
                        <div class="control">
                            <input class="input small-ipt" id="ge-esq" type="number" min="-15" max="0" step="0.25" required>
                        </div>

                        <label class="label lb-mg">
                            Do olho direito:
                        </label>
                        <div class="control">
                        <input class="input small-ipt" id="ge-dir" type="number" min="-15" max="0" step="0.25" required>
                        </div>
                    </div>
                    <div class="container is-fullhd">
                        <p class="title has-text-centered txt-block">Insira abaixo o seu grau cilíndrico</p>
                        
                        
                            <div class="field is-horizontal is-grouped is-grouped-centered block centralize-lt">
                                <label class="label lb-mg ">
                                    Do olho esquerdo:
                                </label>
                                <div class="control">
                                    <input class="input small-ipt" id="gc-esq" type="number" min="-6" max="0" step="0.25" required>
                                </div>
                                
                                
                                <label class="label lb-mg">
                                    Do olho direito:
                                </label>
                                <div class="control">
                                <input class="input small-ipt" id="gc-dir" type="number" min="-6" max="0" step="0.25" required>
                            </div>
                        </div> 
                    </div>
                    <div class="field is-grouped is-grouped-centered top-block">
                        <button class="button is-info" type="submit">
                            Calcular a sua lente ideal
                        </button>
                        <button id="clear" class="button is-dark mgl" type="reset" onclick="document.getElementById('result').innerHTML='...'">
                            Limpar
                        </button>
                    </div>
                    <div class="field is-grouped is-grouped-centered block">
                        <p id="result" class="title is-4 top-block">
                            ...
                        </p>
                    </div>
                    </div>
                </form>
            </div>
        </div>
    </section>
</body>
<script>
    const ge_esq = document.getElementById("ge-esq");
    const ge_dir = document.getElementById("ge-dir");
    const gc_esq = document.getElementById("gc-esq");
    const gc_dir = document.getElementById("gc-dir");

    function calc(){
        if (
            ge_esq.value && ge_dir.value <= -3 &&
            ge_esq.value && ge_dir.value >= -12 && 
            gc_esq.value && gc_dir.value == 0 ||
            gc_esq.value && gc_dir.value >= -2 && 
            ge_esq.value && ge_dir.value >= -10 && 
            ge_esq.value && ge_dir.value <= -3
            )

            {
            console.log("Lente Prime");
            document.getElementById("result").innerHTML = "Lente Prime!"; 
            }
        else if (
                ge_esq.value && ge_dir.value >= -15 &&
                gc_esq.value && gc_dir.value >= -5 &&
                ge_esq.value && ge_dir.value < 0 &&
                gc_esq.value && gc_dir.value < 0
                )
                {
                console.log("Lente Vision");
                document.getElementById("result").innerHTML = "Lente Vision!"; 
                }       
        else{
            console.log("Desculpe, seus dados não se encaixam em nenhuma recomendação...");
            document.getElementById("result").innerHTML = "Desculpe, seus dados não se encaixam em nenhuma recomendação..."; 
        }

        if  (
            ge_esq.value && ge_dir.value == 0 &&
            gc_esq.value && gc_dir.value == 0
            )
            {
            console.log("Sua visão é excelente! Não há necessidade usar óculos...");
            document.getElementById("result").innerHTML = "Sua visão é excelente! Não há necessidade usar óculos...";
        }
    }

    function getGlasses(){
        console.log(ge_esq.value, ge_dir.value, gc_esq.value, gc_dir.value)
        calc();
    }

    function validate(event){
        event.preventDefault();
        getGlasses();
    }
</script>
</html>
