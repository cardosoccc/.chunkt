# prova de redes - resumo

## introdução

- histórico da internet

	- darpa
		- 1968: primeira rede experimental (4 universidades)
		- sistema de comunicação que não pudesse ser interrompido
		- militares americanos durante a guerra fria
		- rede sem central que não pudesse ser destruída

	- especificação tcp/ip
		- 1974
		- vinton cerf e robert kahn

	- rnp
		- 1989
		- rede nacional de pesquisa

- redes de computadores

	- lan
		- local area network
		- 1km

	- man
		- metropolitan area network
		- cidade

	- wan
		- wide area network
		- país, continente

	- internet
		- duas ou mais redes conectadas

	- topologias de rede

		- definição
			- forma como os enlaces físicos e nós estão organizados
			- determinando caminhos físicos entre as estações
			- diferentes relações de custo/desempenho

		- tipos
			
			- ponto-a-ponto

				- estrela
					- estações ligadas a um nó central
					- nó central controla comunicação
					- facilidade de broadcast e multicast
					- problemas de confiabilidade e modularidade
					- switches

				- anel
					- diminui nr. de ligações ponto a ponto
					- único sentido de transmissão
					- mensagem circula entre estações até chegar ao destino
					- sem caminhos alternativos
				
				- totalmente ligada
					- $n$ estações
					- $n \times \frac{(n-1)}{2}$ ligações ponto-a-ponto
					- economicamente inviável
				
				- parcialmente ligada
					- existem caminhos alternativos
					- maior confiabilidade

			- multiponto

				- barramento
					
					- meio de comunicação compartilhado
					
					- : confiabilidade
						- independente de cada nó
						- dependente do mecanismo de acesso ao meio

					- : distância máxima e número de nós

					- repetidores
						- assegurar qualidade do sinal
						- ponto de fragilidade

					- hubs
						- facilitar localização e isolamento de falhas
						- inserção de novas estações no barramento sem parada

## modelo osi e internet

- motivo da divisão em camadas
	- redução da complexidade do sistema
	- isolamento das funcionalidades
	- permite funções específicas
	- cada camada presta serviço para a camada superior

- encapsulamento
	
	- dados passos pelas camadas de cima para baixo no emissor
	
	- de baixo pra cima no receptor
	
	- processos fim-a-fim
		- processo se comunica com outro processo de uma mesma camada

- função de cada camada osi
	
	- : física
		- responsável pela movimentação de bits individuais de um nó para outro
		- representação de bits: elétricos ou óticos
		- taxa de dados: bits por segundo
		- modos de transmissão
			- simples
			- half-duplex
			- full-duplex

	- : enlace
		- responsável pela transferência de quadros
		- transforma a camda física em uma linha confiável e livre de erros
		- faz o enquadramento - divide fluxos recebidos da camada de rede em quadros
		- coloca endereços físicos de origem e destino no cabeçalho
		- deteção e controle de erros
		- : controle de acesso
			- determina qual dispositivo assume controle do link
			- quando dois ou mais estiverem conectados ao mesmo link

	- : rede
		- responsável pela entrega de pacotes individuais
		- desde o host de origem até o host de destino
		- roteamento
			- quando redes ou links estão conectados para criar redes de redes
			- roteadores ou comutadores encaminham ou comutam pacotes para os destinos finais

	- : transporte
		- responsável por entregar uma mensagem de um processo a outro
		- endereçamento de ponto de acesso ao serviço
		- leva a mensagem inteira para o processo correto
		- segmentação e remontagem
			- mensagem é dividida em segmentos e recebe números de sequência
		- controle de fluo e controle de erros fim a fim

	- : sessão
		- responsável pelo controle de diálogo e sincronização
		- controle de diálogo
			- half-duplex
			- full-duplex
		- sincronização
			- permite adição de pontos de verificação/sincronização

	- : apresentação
		- responsável pela sintaxe e semântica da informação trocada entre dois sitemas
		- : tradução
			- traduz informações de um formato específico para um formato comum
		- : compressão
			- reduz o número de bits
		- : criptografia
			- cifrar e decifrar informações

	- : aplicação
		- responsável por prover serviços ao usuário

- função de cada camada tcp/ip
	
	- : física
		- host-para-rede
		- não define nenhum protocolo específico
		- suporta todos os protocolos padrão e proprietários

	- : enlace
		- host-para-rede
		- não define nenhum protocolo específico
		- suporta todos os protocolos padrão e proprietários

	- : rede
		- ip
			- internetworking protocol
			- protocolo sem conexão e não confiável
			- serrviço de entrega do tipo best-effort
			- nenhuma verificação ou correção de erros
			- transporta datagramas
			- não acompanha rotas e nem reordena pacotes

	- : tranporte
		
		- tcp
			- transmission control protocol
			- protocolo de transporte confiável
			- divide fluxo de dados em segmentos

		- udp
			- user datagram protocol
			- protocolo de transporte não confiável
			- sem conexão

	- : aplicação
		- assume tarefas da camada de sessão e apresentação
		- usuário acessando os serviços

- endereços das camadas
	- enlace: mac
	- rede: ip
	- transporte: porta

- osi x tcp/ip

	- número de camadas
		- osi: 7
		- tcp/ip: 5
		- tcp/ip não tem sessão e apresentação
	
	- : complexidade
		- tcp/ip mais simples
		- camada de sessão e apresentação com poucas atribuições
		- osi: padrão técnico inferior, implementaões iniciais lentas
	
## camada física

- sistemas de comunicação de dados
	
	- : emissor
		- entrega um sinal de energia adequado
		- modulador
	
	- : meio
		- propaga a energia entregue pelo emisso até o receptor
	
	- : receptor
		- retira a energia do meio e recupera os símbolos
		- demodulador
	
	- : problemas
		- ruídos
		- distorção
		- atenuação

- tipos de operação
	
	- : simplex
		- do ponto a ao b
		- rádio
	
	- : semi-duplex
		- ambos os sentidos, alternadamente
		- walkie-talkie
	
	- : duplex
		- ambos os sentidos, simultaneamente
		- telefone

- tipos de sinais

	- sinal analógico
		- sinais variam continuamente
	
	- sinal digital
		- sinais tem dois valores elétricos (discretos)

- transformada de fourier
	- permite representar sinais em componentes senoidais

- banda base
	- sinais que vão de 0 até frequência máxima

- banda passante
	- sinais deslocados para ocupar uma faixa mais alta

- largura de banda
	- diferença entre maior e menor frequência
	- hertz: intervalo de frequências que um canal deixa passar
	- bps: velocidade de transmissão de bits em um canal

- teorema de nyquist
	- taxa máxima de transmissão de um canal
	- $c = 2b log_2 v bps$
	- c - capacidade máxima de transmissão em bps
	- b - largura de banda do canal
	- v - quantidade de níveis para codificação do sinal

- bit, dibit, tribit
	- bit: pulso que apresenta dois níveis distintos (0, 1)
	- dibit: pulso com 4 níveis distintos ($v = log_2 4)
	- tribit: pulso com 8 níveis distintos ($v = log_2 8)
	- se um sinal é transmitido na velocidade v
	- exigindo uma faixa b do sistema
	- poderá ser transmitido com a mesma velocidade na faixa b/2 se modificado para dibit 
	- poderá ser transmitido com a mesma velocidade na faixa b/3 se modificado para tribit 

- bit rate (vs)
	- número de bits transmitidos em um segundo
	- eficiência

- baud rate (vm)
	- taxa de sinalização
	- número de unidades de sinal por segundo
	- requeridas para representar tais bits
	- igual ou menor que a bit rate
	- eficiência de transmissão de rede
	- determina a largura de banda

- baud
	- faixa de passagem mínima que o sistema deve possuir
	- para permitir o reconhecimento de uma sequência de pulsos entrantes de duração t
	- deve deixa passar a fundamental do padrão (frequência portadora)
	- $b = \frac{1}{2t}$
	- $vm = \frac{1}{t}baud
	- $vm = 2b$ (o inversp do menor tempo no sinal)
	
	- : exemplo 1 ( 4 bits; 1000 unidades por sec.; qual o bit rate? )
		- sinal analógico carrega 4 bits em cada unidade de sinal
		- se 1000 unidades são enviadas por segundo
		- encontrar baud rate (vm) e bit rate (vs)
		- vm = 1000 baud
		- vs = 1000 * 4 = 400bps
		- vs = baud rate * nr. de bits por unidade de sinal

	- : exemplo 2 ( 6 bits; 3000 bit rate; qual o baud rate? )
		- baud rate = bit rate / bits por sinal = 500 baud

	- : exemplo 3 ( 4 bits; 9600 bit rate; qual a frequência da fundamental de saída? )
		- banda passante - b
		- vm = 9600 / 4 = 2400 baud
		- vm = 2b
		- b = vm / 2
		- 2400 / 2
		- b = 1200 hz
		- apropriado para sinal telefônico (300-3300hz)

- modulação
	- processo por qual se imprime/varia uma informação em uma onda portadora
	- pela variação de um de seus parâmetros (amplitude, frequência, fase)
	- permite a transmissão de várias informações no mesmo meio utilizando frequências diferentes

- demodulação
	- retirada de informação de uma onda portadora

- tipos de modulação

	- : portadora senoidal
		- analógica ou digital

	- : portadora trem-de-pulso
		- analógica ou digital

- tipos de conversão

	- digital-analógica
		
		- ask
			- amplitude shift keying
			- modulação por chaveamento de amplitude
			- força de sinal variada pra representa 0 ou 1
			- frequência e fase permanecem cconstantes enquanto amplitude é modificada
			- altamente susctível a ruído
		
		- fsk
			- frequency shift keying
			- modulação por chaveamento de frequência
			- amplitude e fase permanecem constantes
			- evita mais os ruídos que a ask
			- bluetooth
		
		- psk
			- phase shift keying
			- modulação por chaveamento de fase
			- amplitude e frequência permanecem constantes
			- não é suscetível a degradação por ruído
			- 8-psk
				- cada salto (45 graus) pode representar 3 bits (tribit) e enviar dados 3 vezes mais rápido
				- bit rate = 3 * baud rate
			- wifi
		
		- qam
			- modulação por amplitude de quadratura
			- combinação de ask e psk
			- máximo contraste entre cada unidade de sinal (bit, dibit, tribit)
			- adsl

	- analógica-analógica
		- am: modulação por amplitude
		- fm: modulação por frequência
		- pm: modulação por fase

- multiplexação

	- conceito
		- transmissão simultâneas de múltiplos sinais sobre um único link de dados
		- multiplexador no lado emissor
		- demultiplexador separa o fluxo para os dispositivos receptores
		- permite utilização mais eficiente de recursos

	- : técnicas

		- : fdm
			- por divisão de frequência (analógica)
			- cada sinal é odulado numa frequência diferente
			- rádio broadcast
	
		- : ofdm
			- orthogonal frequency division multiplexing 
			- consiste em enviar a informação modulando em qam ou em psk 
			- um conjunto de portadoras de diferentes freqüências
			- wimax, adsl, tv digital
	
		- : wdm
			- wavelength division multiplexing
			- por divisão de comprimento de onda (analógica)
			- vários feixes de luz em freqüências diferentes
			- transmitidos por fibra óptica

		- : stdm
			- synchronous time division multiplexing
			- por divisão de tempo (digital)
			- taxa de dados do meio excede a capacidade da taxa de dados do sinal digital
			- múltiplos sinais digitais intercalados no tempo

- categorias do meio

	- meio guiado
		
		- com limite físico
		
		- par trançado
			- dois condutores encapados por material isolante
			- um fio carrega o sinal o outro é o terra
			- fios trançados reduzem o efeito da interferência
			- mais tranças = melhor qualidade
		
		- par trançado blindado
			- stp
			- capa metálica para impedir interferência (crosstalk)
			- conector rj45
			- mais caro
			- menos suscetível a ruído
		
		- par trançado não-blindado
			- utp
			- cat3, cat5
			- mais barato
			- flexível
			- fácil de instalar
			- conector rj45

		- coaxial
			- conector bnc
			- largura de banda maior que par trançado
			- atenuação maior (requer mais repetidores)
			- thin ethernet (10Base2)
		
		- fibra ótica
			
			- : vantagens
				- baixo índice de atenuação
				- leves e flexíveis
				- baixa influência de ruídos
				- grande velocidade

			- : desvantagens
				- custo
				- dificuldade de efetuar multiponto
				- perda nas terminações
			
			- : multimodo
				- distâncias menores
			
			- : monomodo
				- diâmetro menor
				- distâncias maiores

			- 1000Base-FX (Fast Ethernet)

	- meio sem fio

		- métodos de propagação
			- ground propagation
			- sky propagation
			- line-of-sight propagation
		
		- sem limite físico
		
		- ondas de rádio
			- omnidirecional
			- broadcasting de longa distância

		- enviados por microondas, satélites e transmissão celular

- modos de transmissão

	- : paralela
	
	- : serial
	
	- : baseband
		- banda de base
		- um único canal
		- explorando toda a faixa do suporte
	
	- : broadband
		- banda larga
		- diversos canais, 
		- dividindo-se a faixa de frequência disponível no suporte 
	
	- : síncrona
		- elementos envolvidos são sincronizados através da utilização de um sinal de clock
	
	- : assíncrona
		-  bits (ou caracteres) de controle para indicar o início e o final das transmissões

## camada de enlace e redes locais

- controle de acesso ao meio

	- protocolos de acesso múltiplo
		
		- : acesso aleatório
			
			- MA
			
			- CSMA
				- estação escuta o meio antes de enviar
				- reduz possibilidade colisões
			
			- CSMA/CD
				- estação envia o frame e entrão monitora o meio
				- se colisão é detectada um sinal jamming é transmitido
				- backoff exponencial determina quando reenviar
			
			- CSMA/CA
				- lans wireless
				- transmissor envia pacotes pequenos com pedido de envio (RTS)
				- estãção de base difunde um clear-to-send (CTS) em resposta
				- CTS ouvio em todos os nós
				- transmissor envia os quadros
				- evita por completo colisões de quadros
		
		- : acesso ordenado
			- reserva
			- polling
			- token passing
		
		- : canalização
			- fdma
			- tdma
			- cdma

- controle de fluxo e erro

	- stop-and-wait arq

		- algoritmo de bit alternado
		- emissor mantém cópia do último frame enviado e espera ack
		- próximo frame é enviado quando o ack é recebido
		- frames perdidos ou corrompidos são reenviados
		- repete-se até o eot
		- simplicidade
		- lento

	- go-back-n arq

		- janela n com retransmissão integral
		- envia múltiplos frames antes de receber um ack
		- especifica série de números de frames que podem ser recebidos
		- receptor inclui número do próximo frame que ele espera receber
		- emissor sabe que todos os anteriores foram recebidos

	- selective-repeat arq

		- janela n com retransmissão seletiva
		- mais eficiente mas requer mais processamento

- detecção e correção de erros

	- teste de paridade
		- camada de enlace
		- um último bit é inserido para garantir paridade par
		- detecta erros isolados
		- se soma dos bits é par, aceita-se

	- crc
		- camada de enlace
		- divisão binária
		- sequência de bits redundantes é anexado ao fim dos dados
		- que depois são usados nos cálculos para detectar o erro
		- polinômios são usados para representar o gerador de crc
		- pode detectar erros em rajadas
		- se resto é zero, aceita-se

	- checksum
		- protocolos de alto nível
		- no emissor os dados são dividos em segmentos iguais de n bits
		- segmentos são adicionados usando aritmética de complemento de um
		- soma é completada e torna-se o cheksum
		- no receptor os dados são dividos em k seções de n bits
		- seções são somadas usando complemento de um
		- soma é complementada
		- se resultado é zero, aceita-se

- enquadramento

	- frames de tamanho fixo (wan)
	- frames de tamanho variável (lan)
	- método orientado a caracter
	- método orientado a bit

- protocolo arp

	- addres resolution protocol
	- cada nó tem uma tabela arp

- ethernet

	- 10Base5
		- coaxial grosso

	- 10Base2
		- coaxial fino

	- 10Base-T
		- par trançado

	- 10Base-F
		- fibra ótica