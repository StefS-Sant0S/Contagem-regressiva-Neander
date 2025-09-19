# Contagem-regressiva-Neander
Programa para realizar contagem regressiva em assembly para o processador Neander.
# Projeto: Algoritmo de Contagem Regressiva em Assembly

**Autor:** Stefany dos Santos
**Disciplina:** Arquitetura computacional
**Ferramenta:** Simulador Neander/X3

---

## 1. O projeto

Este é o código-fonte de um programa de contagem regressiva, desenvolvido Para o processador Neander em linguagem Assembly. O programa é inicializado com um valor numérico pré-definido e, a cada ciclo, subtrai desse valor em uma unidade até chegar a zero, e então finaliza.

---

## 2. Como o Código Funciona?

O cerne deste programa é um **loop condicional**. A lógica por trás da contagem regressiva foi esta:

1.  **Inicialização:** O valor inicial da contagem (ex: 50) é carregado da memória (comando LDA) para o registrador Acumulador (ACC).
2.  **Iteração (O Loop):** O valor atual do Acumulador é subtraído por 1 (comando SUB do DB chamado aqui de UM). Aqui o processador então verifica uma condição, neste caso: "O resultado desta subtração foi zero?".
3.  **Tomada de Decisão (Pulo Condicional):** se o resultado NÃO for zero, o programa recebe a ordem de "pular" de volta para o início do loop, e repete o passo de subtração. Para isso, foi utilizada o comando `JNZ` (Jump if Not Zero). Mas se o resultado for zero, o pulo não acontece e o programa continua para a próxima linha, que é o comando de parar sua execução.
4.  **Finalização:** A instrução `HLT` (Halt) é executada, e encerra o programa.

Para possibilitar a visualização do processo, a cada ciclo do loop o valor atual do Acumulador (ACC) é armazenado em uma posição específica da memória, permitindo acompanhar a contagem regressiva pela opção "passo a passo" no neander.

---

## 3. Instruções e comandos Assembly Utilizados

Cada linha de código tem um propósito específico aqui:

- `LDA INICIAL`: **(Load Accumulator)** Carrega o valor inicial da contagem (definido em `INICIAL`) para o registrador ACC.
- `STA ATUAL`: **(Store Accumulator)** Armazena o valor que está no ACC na posição de memória `ATUAL`. É o que nos permite ver o número diminuindo.
- `SUB UM`: **(Subtract)** Subtrai o valor contido na posição de memória `UM` (que é 1) do valor atual do ACC.
- `JNZ LOOP`: **(Jump if Not Zero)** A instrução mais importante. Se o resultado da última operação (`SUB`) não foi zero, o fluxo do programa é desviado de volta para o rótulo `LOOP`.
- `HLT`: **(Halt)** Para completamente a execução do processador.
- `DB`: **(Define Byte)** Não é uma instrução, mas uma diretiva para ocompilador. Reserva um espaço na memória e insere um valor nele. Usa-se para definir os números iniciais.

---

## 4. Como Executar e Testar o Programa

Para rodar este projeto, siga os passos abaixo:

1.  Baixe o arquivo `contagem_regressiva.nef` deste repositório.
2.  Inicie o programa Neander/X3 em seu computador.
3.  Dentro do simulador, utilize o menu **Arquivo > Abrir** para carregar o arquivo `.nef` que você baixou.
4.  Clique no botão **Compilar** na barra de ferramentas. A janela de "Saída da compilação" deve mostrar "0 erros encontrados".
5.  Para observar cada passo da execução, clique repetidamente no botão **"Passo a passo"**. o valor no registrador `ACC` e na posição de memória `ATUAL` diminuirá a cada ciclo.
    Para rodar tudo de uma vez, clique em **"Executar"**.

### Como testar com um valor diferente?

Para iniciar a contagem com outro número,é necessário editar o código-fonte antes de compilar:

- Altere o valor na linha: `INICIAL: DB 50`
- Troque `50` por outro número.
- Compile e execute novamente.


**O objetivo principal deste projeto é demonstrar na prática alguns conceitos fundamentais da programação chamada de baixo nível. Como por exemplo a manipulação de registradores, acesso à memória ,e a implementação de estruturas de controle de fluxo, a exemplo os laços de repetição (loops).

