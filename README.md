# redes_e_sistemas_curso_ada

*Nesse documento apresento meus aprendizados no módulo de Redes e Sistemas da **Ada Tech**.*

## O que é Redes?

São dois ou mais dispositivos eletronicos conectados entre si, que trocam informações por uma linguagem pré-estabelecida chamada protocolo.
Essa conexão pode ser feita de duas formas:
* física: cabo coaxieal ou fibra óptica;
* via wireless: através de rádio frequência, Bluetooth ou infravermelho.

### Qual a sua Origem?

Na guerra fria a *Darpa* (pesquisa militar americana) procurou ampliar suas pesquisas se conectando a universidades.
Com isso, as universidades americanas começaram a se comunicar com outras universidades de outros países e para que houvesse uma comunicação viável criaram-se orgãos reguladores que desenvolviam protocolos de redes.
Assim, viabilizaram que o mercado privado expandisse a capacidade de processamento das redes tornando o que temos hoje possível.

### Principais equipamentos de redes (infraestrutura)

* NIC (Network Interface Card): placa de computador que nos conecta a internet via Wirelesse e cabo Ethernet
* Hub: conecta diferentes dispositivos via cabo, porém não traz privacidade entre eles. - se tornou obsoleto
* Switch: conecta vários diferentes dispositivos via cabo e consede privacidade através do ponto a ponto. - substituiu o hub e escalou maior a possibilidade de acesso a rede
* Roteador: ele procura as melhores rotas de internet para entregar os pacotes do remetente ao destinatário no menor tempo possível. 
* Modem: modula e demodula o sinal de internet dando acesso aos que estiverem conectados nele. Ele faz o papel dos três dispositivos anteriores.

### Cabeamento Estruturado
Existem padrões de como os cabos de redes devem ser feitos e estruturados possibilitando melhor organização e performance de redes. São essas normas:

* NBR 14.565
* ANSI/TIA 568
* ANSI/TIA 569

Tipos de cabos:

* Cabos de partrançado: o mais comum com 8 fios que transmitem. Esses cabos podem ser blindados (STP) ou não (UTP).
* Cabo coaxial: possui maior revestimento e é muito usado para Tv.
* Cabo de fibra óptica: composto por vidro em seu interior permitindo que os dados sejam passados por luz.

Toda essa infraesturura para que esteja organizada é colocada em um RACK com switchs etc.

## Modelo OSI e TCP/IP

Padrão de comunicação nas redes.

### Modelo OSI

Sua estrutura é dada pelas seguintes 7 camadas: FÍSICA, ENLACE, REDES, TRANSPORTE, SESSÃO, APRESENTAÇÃO, APLICAÇÃO.

1. Física: é por onde os dados são transmitidos, cabos, modens, servidores etc.
2. ENLACE: aqui é verificado se o pacote tem algum erro antes de ir pras camadas superiores, além de controlar o fluxo de que os dados são transmitidos.
3. REDES: aqui ocorre o empacotamento e envio de um roteador para outro.
4. TRANSPORTE: conecta com o destino final podendo ser através dos protocolos TCP/IP ou UDP.
5. SESSÃO: aqui é estabelicido como será a comunicação com o destino e por quanto tempo.
6. APRESENTAÇÃO: criptografa o nosso dado que vem da aplicação ou descriptografa o dado da Sessão para enviar a Aplicação.
7. APLICAÇÃO: contém as informações do DNS (site) ou do SSH que se deseja comunicar.

Camadas 5,6 e 7 são as camadas que o usuário tem maior acesso e consegue modificar. A partir da cada Física para a de transporte quem determina é o hardware.

### Modelo TCP/IP

Possui 4 camadas em sua estrutura: ACESSO e REDE, INTERNET, TRANSPORTE e APLICAÇÃO.

1. ACESSO e REDE: corresponde as camadas Físicas e de Enlace do modelo OSI.
2. INTERNET: corresponde a camada de Redes do modelo OSI.
3. TRANSPORTE: corresponde a camada de Transporte do modelo OSI.
4. APLICAÇÃO: corresponde as camadas de Aplicação, Apresentação e de Sessão do modelo OSI.

Esses modelos têm como objetivos tornar padrão a comunicação entre dispositivos para que não haja conflitos e impossibilite o uso da internet.



