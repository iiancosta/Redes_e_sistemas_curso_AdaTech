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

#### IPV4 e IPV6

* IPV4: formado por 32 bits dividido por 8 octetos onde cada octeto onde cada octeto pode variar de 0 a 255. Exemplo: 192.168.0.1
Diante a defazajem do IPV4, o NAT interveio gerenciando o IP público e local, onde vários dispositivos que estão em uma mesma rede utilizam o mesmo IP público.

* IPV6: formado por 128 bits dividido em 16 pares em formato hexadecimal. Exemplo: 1050:0000:0000:0000:0005:0600:300c:326b 
O IPV6 veio para sanar a limitação de seu antecessor com um número extraordinário de IPs. Com isso podemos ter conexões P2P (Peer-to-Peer) dando mais controle de acesso, confidencialidade, integridade de dados, entre outras benefícios.

#### Cálculo de sub-rede

Para colocar as sub-redes em prática é importante que se entenda a respeito das classes de endereço IP:


| Classe |   1° Octeto   | Exemplo de IP |   Rede/Host   |    Máscara    | N° de Redes | Endereços por Rede |
|:------:|:-------------:|:-------------:|:-------------:|:-------------:|:-----------:|:------------------:|
|   A    |     1-126     |   10.0.0.1    |    R.H.H.H    |  255.0.0.0    |     126     |     16,777,214     |
|   B    |    128-191    |  172.16.0.1   |    R.R.H.H    | 255.255.0.0   |    16,382   |       65,534       |
|   C    |    192-223    |  192.168.0.1  |    R.R.R.H    | 255.255.255.0 |   2,097,150 |         254        |
|   D    |    224-239    |   239.0.0.1   |   Multicast   |       NA      |      NA     |         N/A        |
|   E    |    240-255    |255.255.255.255| Experimental  |       NA      |      NA     |         N/A        |


**1. Máscara de Sub-rede:**
   - Imagine a máscara de sub-rede como um filtro que separa o endereço IP em duas partes: a parte da rede e a parte dos dispositivos (hosts).
   - Exemplo: Se a máscara de sub-rede for 255.255.255.0, isso significa que os primeiros três conjuntos de números no endereço IP são para a rede, e o último conjunto é para os dispositivos.

**2. Endereço IP da Sub-rede:**
   - Cada sub-rede tem um endereço IP específico, geralmente atribuído ao roteador que a conecta à rede principal.
   - Este endereço IP é fundamental para o roteamento entre sub-redes.

**3. Número de Hosts:**
   - A quantidade de dispositivos que podem ser conectados à sub-rede é determinada pelos bits dedicados aos hosts.
   - Alguns endereços são reservados, então a fórmula é \(2^{\text{número de bits para hosts}} - 2\).

* Exemplo Numérico:

Se tivermos uma máscara de sub-rede que reserve 8 bits para hosts, a fórmula seria \(2^8 - 2 = 254\). Isso significa que há 254 endereços disponíveis para dispositivos naquela sub-rede.

## Domínio, DNS e Latência

* **Domínio** é o nome que damos a um endereço IP que usamos na internet para acessar um site. Como exemplo temos o github.com ou google.com e por traz de cada um há um endereço IP usado para localizar acessar os sites.
O protocolo que faz essa cobertura e comunicação é o **DNS**.

A estrutura de um endereço web:

|   Protocolo  | Subdomínio | Domínio | Top-Level Domain |      Caminho       |    Parâmetros   |  Âncora   |
|--------------|------------|---------|------------------|--------------------|-----------------|-----------|
|   https://   |    www.    | openai  |       .org       | /technology/gpt-3/ | ?id=123&lang=en | #section-2|

* **Latência** é o tempo que leva para minha requisição ir até o destino e retornar com a resposta. Uma alta latência significa demora ao acessar sites ou solicitações desejadas. Para solucionar isso, foi desenvolvido o cache, armazenando recursos desejados em servidores próximos. Após o primeiro acesso a um recurso, um cache é criado para permitir acesso mais rápido em buscas subsequentes.

## Comandos de configuração de Redes no prompt comand

* ipconfig, ipconfig \ flushdns, ping, nslookup, tracert, rout print, netstat

1. **ipconfig:**
   - Exibe informações sobre configuração de rede em sistemas Windows, como endereço IP, configuração de DNS, gateway padrão, entre outros.

2. **ipconfig \ flushdns:**
   - Limpa o cache DNS do sistema Windows. Isso remove as entradas de resolução de nomes armazenadas em cache, permitindo atualizações e novas resoluções.

3. **ping:**
   - Testa a conectividade entre dois dispositivos na rede. Envia pacotes para um endereço IP específico e mede o tempo que leva para a resposta, verificando a disponibilidade e a latência da conexão.

4. **nslookup:**
   - Usado para consultar servidores de nomes para obter informações sobre resolução de DNS, como endereço IP associado a um nome de domínio ou informações sobre servidores DNS.

5. **tracert:**
   - Rastreia a rota que os pacotes de dados seguem da origem ao destino na rede. Mostra os saltos entre roteadores e o tempo de resposta de cada salto.

6. **route print:**
   - Exibe a tabela de roteamento do sistema operacional, mostrando os destinos de rede, gateways e interfaces de rede associadas a eles.

7. **netstat:**
   - Exibe estatísticas de conexão, portas abertas, roteamento, interfaces de rede ativas e outras informações detalhadas sobre a conectividade de rede do sistema.

## Segurança da Informação

### Segurança Física:
- **Refrigeração:** Garante a temperatura adequada para o funcionamento dos equipamentos e evita a perda de dados.
- **Backup:** Cópia de segurança dos dados para recuperação em caso de falha ou ataque.
- **Redundância de rede:** Uso de caminhos alternativos para manter a conexão em caso de falhas no provedor.
- **Load Balancing:** Distribuição de carga entre servidores para otimizar o desempenho.
- **Acesso biométrico:** Restringe o acesso autorizado usando características físicas únicas.
- **Desativar acesso via pen drive:** Medida para prevenir a introdução de ameaças via dispositivos USB.
- **Atualização do sistema operacional:** Instalar patches e atualizações para fechar vulnerabilidades.
- **Senhas complexas:** Fortalece a segurança de dispositivos e sistemas.
- **Onde guardar senhas:** Cofres físicos (HSM) ou virtuais (vaults) para armazenamento seguro.

### Segurança Lógica:
- **Single Sign-On (SSO):** Acesso único a várias aplicações com uma única credencial.
- **Firewall e normas de ACL:** Regras para controlar o tráfego na rede e filtrar pacotes.
- **Conexões VPN:** Redes privadas virtuais para comunicações seguras.

### Ataques de Segurança:
- **DoS (Denial of Service):** Sobrecarrega um sistema para torná-lo inacessível.
- **DDoS (Distributed DoS):** Utiliza múltiplos sistemas para sobrecarregar um alvo.
- **Ransomware:** Bloqueia ou criptografa dados e exige resgate para liberá-los.


## Para por a mão na massa

Faça o curso Começando com o Cisco Packet Tracer.



