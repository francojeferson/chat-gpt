# chat-gpt

**Objetivo**: praticar com API oferecida pela OpenAI utilizando interface de acesso à inteligência artificial.

**Arquivo HTML** - index.html
- possui uma `div` contendo duas tags `textarea` e um `button` para enviar perguntas à API
- o primeiro `textarea` deve ser usado para exibir as respostas retornadas pela IA
- o segundo `textarea` deve ser usado para que o usuário adicione a pergunta
- o `button` deve enviar a função para o método POST da API

**Arquivo CSS** - style.css
- possui estilização simples e objetiva

**Arquivo JS** - script.js
- possui referência dos elementos HTML utilizando ID em variáveis
- a variável `inputPergunta` recebe elemento ID `inputPergunta` e deve ser usado para ler o valor fornecido pelo usuário
- a variável `resultadoIA` recebe elemento ID `resultadoIA` e deve ser usado para exibir o resultado da pergunta para o usuário

> **IMPORTANTE**: para obter a chave da API, é necessário seguir os passos no link: https://platform.openai.com/account/api-keys
>
> A chave contida neste projeto deve ser destruída e substituída a cada 30 dias

- função EnviarPergunta:
    - deve armazenar o valor da pergunta em uma variável
    - deve fazer o `fetch` com a API do OpenAI utilizando o formato [completions](https://platform.openai.com/docs/api-reference/completions/create)
    - deve utilizar o `then` para transformar a resposta em JSON
    - deve pegar o JSON no próximo `then` e fazer validações:
        - primeiro `if`: se o `resultadoIA` possuir valor, deve quebrar linha
        - segundo `if`: se ocorrer algum erro com o JSON, deve imprimir em tela; se não possuir erro, deve exibir a resposta enviada pela API através de array; para o caso de array vazio, deve aparecer `Sem resposta`
        - por fim, sempre que enviar uma questão, o scroll do elemento ID `resultadoIA` é movido para o fim da tela
    - se qualquer condição retornar erro, deve chamar `catch` e imprimir erro no console
    - após passar nas validações (ou retornar erros), a chamada `finally`:
        - deve zerar a string `Carregando...` do `inputPergunta`
        - deve habilitar o `inputPergunta`
        - deve dar `focus` no `inputPergunta`
    - ao terminar a chamada da API, deve tratar o retorno:
        - último `if`: se o elemento possuir algum valor, deve adicionar três linhas em branco
        - em seguida, deve adicionar uma nova linha de texto que começa com `Eu:` seguido do conteúdo na variável `valorPergunta`
        - depois, o valor do elemento ID `inputPergunta` deve ser alterado para `Carregando...`
        - por fim, o elemento ID `inputPergunta` é desabilitado
    - na última linha da função, o scroll do elemento ID `resultadoIA` é movido para o fim da tela

- chamada da função EnviarPergunta:
    - chama elemento ID `EnviarPergunta` através da lógica do clique em `button`
