Painéis ou Módulos, como preferirmos chamar:
A feature de  Acompanhamento de Fluxo de Processos da Orbitta. 

A adaptação para a Berzerk conta com  fluxo de produção têxti/fabril/controle de estoque/ acompanhamento financeiro/ medição de kpis / cadastramento / controle de confecçãol:

1- Registro de Programação e Alocação de Tecido:
- Utilizado para registrar romaneios enviados pelas malharias e Alocação em Confecções apropriadas ao produto:
- Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP. 
  em funcionamento no webapp e migração para lovable
   aba/csv de apoio: produto_consumo_custo
   aba/csv de log: entrada_destinacao_tecido
  regra do negócio:
 programação + input sistema c/ romaneio/nota fiscal + agendamento de pagamento e     recebimento


2- Controle de Recebimento de Tecidos e Enfesto + Corte:
- Utilizado para receber os tecidos/insumos e Enfestar, Cortar e Expedir para Confecções
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP. 

  em funcionamento no webapp e migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido
 aba/csv de log: entrada_destinacao_tecido e log_corte



3- Controle de Confecções:
- Utilizado para acompanhar a entrega na confecção e o Status de costura.
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP.
Confecções> Acesso externo> Somente visualiza dados relacionados a ele


  em funcionamento no webapp e migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido e log_corte
 aba/csv de log: entrada_destinacao_tecido e log_corte e log_confeccao




4- Registro de Recebimento de Produto e Movimentação de Estoques:
- Utilizado para registrar o recebimento,  conformidade, alimenta pulmões e acompanha movimentação interna
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP, Qualidade, Estoque. 


  em funcionamento no webapp e migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido
 aba/csv de log: entrada_destinacao_tecido e Log Estoque Total (além das próprias abas de cada tipo de movimentação) 



6- Logística:
- Utilizado para  acompanhar a entrega e retirada nas confecções e entrega no estoque BZK
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP, Qualidade, Estoque. 


  em funcionamento no webapp e migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido e log_corte
 aba/csv de log: entrada_destinacao_tecido e log_corte e log_confeccao e Log logística 

7- Cadastros:
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP, Qualidade, Estoque. 
  migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido e log_corte
 aba/csv de log: entrada_destinacao_tecido e log_corte e log_confeccao e Log logística, skus_internos, mapaSKU (usamos essas abas na lógica)
validacao_suspensa , produto_consumo_custo, usuarios_senhas, matriz_fornecimento: (somente para buscar e montar perfis no cadastro automaticamente) e alimentar a table oficial que guardará esses dados de usuário e senhas


8-  Pick and Packing::
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, Corte, PCP, Pick and Packing
  migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido e log_corte
 aba/csv de log: entrada_destinacao_tecido e log_corte e log_confeccao e Log logística e Log Pick And Packing

9-  Módulo Dashs e Estoques Inteligentes:
Política de Acesso: Perfis de Acesso permitidos> Administradores, CEOS, Administrador leve, PCP, Compras> Visualizam informações financeiras
Perfis> Corte, Pick and Packing, Qualidade, Estoque> Não visualizam informações financeiras.
  migração para lovable
 aba/csv de apoio: produto_consumo_custo e entrada_destinacao_tecido e log_corte
 aba/csv de log: entrada_destinacao_tecido e log_corte e log_confeccao e Log logística e Log Pick And Packing

Explicando a usabilidade de cada módulo/painel e suas premissas:

painelTecido, focado em dar entrada em romaneios, premeditar o número de cortes por partidas, pré-criar OPs e destinar tecido a seu devido local de Corte e Costura. 

O painel login para usuários de PCP, Administradores, CEOs, C-Level.
. As informações cruciais pedidas são:

📥Tipo de Entrada: Programada ou Não Programada
Rastreando nossas programações ou tecidos pedidos fora dela.
Malharia
Rastreando o que entrou de cada uma e quanto/quando pagar
Produto
Quais produtos serão gerados, quanto estimado receber
Malharia
Rastreia qual malharia prometeu programação e romaneio de que
Romaneio/NF
Auxilia no rastreio da documentação fiscal/financeira
Data
Organiza o fluxo planejado e real de recebimento
Responsável
Quem deu entrada no romaneio 






O menu segue com a exibição dos tecidos relacionados a partir do Produto selecionado: Isso ajuda o usuário a planejar melhor a entrega de todos os insumos relacionados ao produto, indicando KGs e Rolos de cada insumo necessário. 



O input dessas informações é transformado pelo sistema num resumo pragmático e visual, que apresenta a necessidade de viés de acordo com a quantidade de tecido principal escolhido para a categoria (top-camisetas) e faz o mesmo para os insumos de (bottom-shorts) por exemplo.:



De acordo com o número de partidas informada para o romaneio lá no Contexto inicial, abre-se os campos para que o usuário informe o ID partida (número da partida) e a quantidade de rolos de cada partida> O Sistema busca na aba produto_consumo_custo qual a quantidade de rolos máxima por enfesto/corte para aquele produto e pré-cria OPs baseada nessa quantidade de cortes e num padrão rastreável que identifica: mês, tecido, cor, id partida e número de cortes, facilitando a alocação imediata para cada confecção apta ao produto:



Por fim o usuário determina o primeiro destino do tecido, ou seja para o local de recebimento (que normalmente é o corte):



E ao registrar entrada todas as informações vão para o log na aba “entrada_destinacao_tecido”, cujo cabeçalho completo de A até AN:




Data Registro
O sistema grava a data 
ID Entrada
O sistema cria IDs de entrada único
Tipo Linha
Mãe ou Detalhe: Sendo mãe com a info total do romaneio e detalhe com as partidas e suas respectivas OPs criadas de acordo com a quantidade de rolos max corte por produto
Tipo Entrada
Programada ou Não
Produto
Qual produto vai ser confeccionado
Malharia
Qual malharia responsável
Cor
Qual cor
Tecido
Qual tecido
Romaneio
Romaneio/NF para rastreamento fiscal/financeiro
Data Envio
Data de envio do romaneio 
Responsável
Quem imputou o romaneio no sistema
KG Principal
Quantidade de KGs do tecido principal do produto
Rolos Principal
Quantidade de rolos principais 
KG Complementar
Quantidade de KGs de tecido complementar indicado ao produto
Rolos Complementar
Quantidade de rolos complementar
KG Aviamento
Quantidade de KGs de aviamento
Rolos Aviamento
Quantidade de Rolos de Aviamento
KG Ribana
Quantidade de ribana em KG
Rolos Ribana
Quantidade de ribana em Rolo
PCS Estimadas
PCs estimadas olhando para consumo por kg / por kg principal
Total KG
Total de KGs de todos os insumos
Total Rolos
Total de rolos de todos os insumos
Valor Total s/ Viés
Valor total sem contar viés
KG Viés
KGs de viés indicado pelo sistema
Rolos Viés
Rolos a separar para viés
Valor Viés
Valor do viés
Valor Final
Valor final de tecido/insumo/aviamento/viés
Data Vencimento
Data de vcto da malharia
Status Ribana
Status de se a ribana contempla 5% do kg principal ou não
Cortador
Qual destino receberá o tecido
OP
OP pré-criada
Confecção
Qual confecção alocada
ID Partida
Qual a ID da partida
Corte #
Quantidade de cortes no padrão 1/1 e 1/3
Total Cortes
Total de cortes daquela partida
Status Recebimento Tecido
Se foi recebido no corte e quando
Status Corte
Se foi cortado enfestado, recebido e etc
Entrega Confecção
Se foi entregue e recebido pela confecção
Retorno confecção
Se retornou da confeccção
Entrega Bzk
Se foi entregue completo na BZK e quando



Esse painel fornece todos os insumos necessários e gatilhos para ativar o painelCorte, onde funcionaremos em dois módulos:
Recebimento de Tecido
Enfesto e Corte. 

O usuário de painelCorte deve acessar seu painel e verificar num resumo simples BBE (Boas vindas baseada em evidências- Lógica da Orbitta):

- Boas vindas usuário tal, hoje é dia _/_/_! Mais um dia na Orbitta da Berzerk:


🧶 Tecidos recebidos no Corte: Deve olhar para três opções para responder a pergunta: aba entrada_destinacao_tecido coluna AJ as linhas que contiverem “Recebido no corte”, AK “Tecido Recebido” objetivol é apresentar a quantidade de rolos recebidos no corte olhando para entrada_destinacao_tecido coluna M rolos principais olhando para o tipo MÃE para não duplicar info já que duplicamos pela lógica inicial as linhas de partida e isso pode confundir a script.
✂️ Tecidos já enfestados e cortados: Aqui usamos o log_corte como referencia, olhando para a quantidade de rolos coluna AA “Rolos Enfestados”. 
🕗 Tecidos aguardando corte:  Olhamos para a coluna Q “Rolos partida” e subtraímos da coluna AA “rolos enfestados” respondendo quais rolos aguardam corte. 
📦 Tecidos aguardando recebimento: Olhando para entrada_destinacao_tecido e procurando na coluna AJ e AK o que não contém “recebido no corte”, “tecido recebido”, “cortado” ou “recebido na confeccção”, ou seja, o que está vazio “”. 

O usuário seleciona então o modo de operar, agora que ele já tem uma visualização focada em evidências:




Por inteligência, apresentamos assim que ele seleciona o módulo as informações pertencentes ao módulo que chamamos na Órbita de (FFE- filtragem focada em evidências), isso ajuda o usuário a ser mais assertivo em suas escolhas, ou seja, ele seleciona “Recebimento de Tecido” e já mostramos abaixo do seletor um resumo amigável, intuitivo e voltado para data driven:
- Malharias que aguardam recebimento, quantos romaneios e quantas partidas. Num formato similar a:


Malharia
Romaneio
Rolos
Cores
Partidas
XT
66909
144
Preto, Branco, Verde
4
XT
66908
30
Preto
1
Urbano
567890
120
Chumbo, Vermelho
2


E após esse resumo oferecemos o dropdown de malharia e tecido para que o usuário possa verificar o resumo novamente isolado, ou seja filtrado pro exemplo dele e já disponibilizado no dropdown no formato:

XT- Romaneio 66909- 144 Rolos (Preto, Branco, Verde) 4 Partidas. 

Daí ele afirma o recebimento após emitirmos o resumo de recebimento ao usuário:
- Usuário fulaninho, afirma o recebimento de:

XT- Romaneio 66909- 144 Rolos (Preto, Branco, Verde) 4 Partidas. 
Partida A- 20 Rolos Verde
Partida B- 20 Rolos Preto 
Partida C- … etc

O usuário confirmando: as informações vão para o log_corte colunas A até T, buscando tanto de entrada_destinacao_tecido quanto do próprio input do usuário.




Data Registro	
A
Data em que foi registrado a inputação
Tipo de Acesso	
B
Se vai Receber um Tecido ou Cortar e Enfestar 
Usuário	


C
Responsável por dar aquele input no sistema
Malharia	
D
Referida no Romaneio
Tecido	
E
Referida no Romaneio
Cor	


F
Referida no Romaneio
Produto	


G
Referida no Romaneio
Romaneio/NF	
H
Referida no Romaneio
Conformidade	
J
Se o que está referido no romaneio é Conforme ou não
Aferição de Pesagem/Gramatura	
K
Se vai pesar ou não
"Comprovante e Decisão- 5 - Tipo 5"	
L
Comprovante de decisão em dar entrada e pesar ou opção pela não aferição.
Gramatura	
M
Se aferida pelo usuário
Aferição de Peso dos Rolos	
N
Se aferida pelo usuário
Rolos Total	
O
O mencionado no romaneio em MÃE para aquela cor
Numero de Partida
P
Quantidade de partidas daquele romaneio
	ID Partida	
Q
Informado em entrada_destinacao_tecido e confrontado no frontend pelo usuário
Rolos Partida	


R
Informado em entrada_destinacao_tecido e confrontado no frontend pelo usuário
OPS vinculadas	
S
Uma linha nova é criada ou replicada de acordo com entrada_destinacao_tecido vinculando a exata OP destinada aquele tecido
Num de Cortes Recomendado



T
O número de cortes que foi gerado pelo sistema 


No modo Enfesto e  Corte: Um RVA (Resumo visual alinhado à evidências)- Sistema Órbitta deve ser exibido, novamente baseado em evidências colhidas nas fontes corretas, agora temos log_corte como a principal fonte de info para este modo de operação. Olhando para a coluna K de log_corte devemos nos orientar observando o Comprovante de Decisão 5 (que podemos renomear para Comprovante de Status de Modo de Operação, que representa a escolha do usuário, então exibe um resumo abaixo do dropdown da escolha 


🧵Tecido recebido no Corte: X Rolos (Busca na coluna Q- Rolos Partida)
⏳Aguardando corte: X Rolos (Busca na Coluna B- Recebimento- Tecido)
✂️ Cortados: X Rolos - X PCs (Busca Rolos Enfestados coluna AA)

🧩Partidas aguardando Enfesto/Corte: Apresenta ao usuário o que ainda não tem status “Enfesto + Corte” coluna B e está como status coluna B “Recebimento- Tecido) ou seja, os mesmos dados de “Aguardando corte” no resumo, mas dessa vez em detalhe e apresentando a confecção (que deve ser garantida no log_corte), mas também está disposta em entrada_destinacao_tecido, bem como as OPs vinculadas.



ID Partida
Malharia
Tecido
Cor
Qtd Rolos
Confecção Destino
Qtd Cortes Indicada
OP
ABC1
XT
Cotton
Preto
45
MATHEUS
1/1
OPCTPRABC1-1/1-MT
ABC2
XT
Cotton
Branco
40
JAPONÊS
1/2
OPCTBCABC2-1/1-JP
ABC2
XT
Cotton
Branco
40
MAELE
2/2
OPCTBCABC2-1/2-ML
ABC3
XT
Cotton 
Preto
30
SEM ALOCAÇÃO
1/1
OPCTBCABC3-1/1-NA1



Após o resumo exibido com as partidas que aguardam enfesto e corte, o usuário seleciona qual partida (ou quais partidas- podendo ser mais de uma) ele deseja dar entrada no processo de enfesto e corte:



⭐ Expectativa de Aproveitamento
Expectativa em PCs: 3174
(Aqui devemos exibir a estimativa de PCs que puxamos de entrada_destinacao_tecido coluna T - PCS Estimadas)
Aproveitamento Esperado:3 PCs por Kg.
( o cálculo automático que divide o KG principal referido para aquela partida coluna L entrada_destinacao_tecido por PCS Estimadas coluna T entrada_destinacao_tecido, exemplo (962kg/3174pcs=0,303g), então 1/0,303=3 PCs por KG. 

Upload do Arquivo de Risco (opcional):
O usuário pode fazer upload do risco que vai para esta pasta no drive, mas o objetivo na V2 é ler o arquivo do  risco padrão aqui e fazer o input de folhas e grade automaticamente, eximindo essa necessidade do usuário, de qualquer forma uploadando o risco ou não, ele segue respondendo a pergunta obrigatória: Quantos rolos enfestados? 

Ainda que a partida tenha 90 rolos, se ela foi dividida em dois cortes pela lógica de “máximo de rolos por corte aplicada no painelTecido> se inferior ou igual à máxima= 1, se maior que a máxima (divide a quantidade de rolos da partida pelo máximo de rolos do corte em produto_consumo_custo e arredondado para número inteiro o resultado), ou seja, o usuário pode cortar menos rolos do que foi informado na partida, então exemplo se foi 90 rolos> ele cortou 45, se apresenta 90, ele informa 45 e segue. 

Informa o número de folhas, e a grade, onde aplicamos a regra de calculo e exibição automática para o usuário no front enquanto ele digita: número de rolos enfestados, número de folhas, número de grade por tamanho. 

Objetivo: Calcular e exibir o número total de peças por enfesto, bem como a distribuição dessas peças por tamanho (P, M, G, GG, XG, etc.), com base no número de folhas e na "grade" de tamanhos informados pelo usuário.

1. Entradas do Usuário:
Número de Folhas: Um campo de entrada numérico onde o usuário digita a quantidade de folhas no enfesto.
Grade de Tamanhos: Múltiplos campos de entrada numéricos (ou um seletor/dropdown para cada tamanho P, M, G, GG, XG, etc.) onde o usuário informa a quantidade de cada tamanho na grade. Por exemplo, 3 para P, 3 para M, etc.

2. Lógica de Cálculo (Backend ou Frontend JavaScript):
Essa lógica pode ser implementada diretamente no frontend usando JavaScript para uma resposta imediata enquanto o usuário digita, ou no backend se houver a necessidade de validações adicionais ou persistência de dados. A abordagem frontend é geralmente preferível para feedback instantâneo.
Passo a Passo:
A. Obter os Valores de Entrada:


numeroDeFolhas: O valor do campo "Número de Folhas".
gradeDeTamanhos: Um objeto ou array contendo a quantidade de cada tamanho (e.g., {P: 3, M: 3, G: 3, GG: 3, XG: 0}).
B. Calcular o Número Total de "Tamanhos" na Grade:


Some a quantidade de cada tamanho presente na gradeDeTamanhos.
totalTamanhos = gradeDeTamanhos.P + gradeDeTamanhos.M + gradeDeTamanhos.G + gradeDeTamanhos.GG + gradeDeTamanhos.XG (adapte para incluir todos os tamanhos relevantes).
C. Calcular o Total Estimado de Peças (PCs) no Enfesto:


totalPCsEnfesto = numeroDeFolhas * totalTamanhos
D. Explodir (Distribuir) as Peças por Tamanho:


Para cada tamanho na gradeDeTamanhos, calcule a quantidade de peças desse tamanho no enfesto.
pecasPorTamanho.P = numeroDeFolhas * gradeDeTamanhos.P
pecasPorTamanho.M = numeroDeFolhas * gradeDeTamanhos.M
pecasPorTamanho.G = numeroDeFolhas * gradeDeTamanhos.G
pecasPorTamanho.GG = numeroDeFolhas * gradeDeTamanhos.GG
pecasPorTamanho.XG = numeroDeFolhas * gradeDeTamanhos.XG

3. Exibição Automática no Frontend (JavaScript):
Event Listeners: Adicione "event listeners" (por exemplo, onkeyup ou onchange) aos campos de "Número de Folhas" e a todos os campos da "Grade de Tamanhos".
Função de Cálculo e Atualização: Sempre que um desses campos for alterado, chame uma função JavaScript que:
Recupere os valores atualizados dos campos.
Execute a lógica de cálculo descrita no Ponto 2.
Atualize os elementos HTML de exibição com os resultados.
Se o corte bate com a estimativa:
Exibe o resumo completo pro usuário confirmar>
- Malharia, tecido, produto, cor, partida e quantidade de rolos recebidos VS enfestados= rolos cortados. 
- Expectativa inicial e aproveitamento inicial (PCS Estimadas e o aproveitamento que já calculamos no próprio frontend) VS Corte Real Total, Corte por Tamanho e Aproveitamento real. Quantidade de folhas, Grade exibida no padrão “3P, 3M, 2G”.


O usuário escolhendo que não bateu com a estimativa, abre os campos pra ele digitar quantidade por tamanho um por um para somar total e então apresenta isso no resumo também no formato acima. Grava no log_corte das coluna K alterando a linha e não duplicando ela para registrar nova info, altera o status para “✅ Enfesto + Corte registrado”, também altera o tipo de acesso na coluna B > Enfesto + Corte e data de registro porém fica intacta preservando a primeira movimentação daquela linha/op/partida, a data alterada então é a da coluna Z marcando início de enfesto e AF marcando fim, e AG que grava então a movimentação, a AH grava o comprovante de decisão que podemos alterar o nome para “Comprovante de aproveitamento”



Arquivo Risco
U
O link do drive da pasta e da img/pdf
resumo de folhas e quantidades
V
resumo no padrão- X FOLHAS- X PCS
Junção de CorteOP
W
Se o usuário optar por UNIR ops para otimizar corte
Formulário decisão do usuário
X
Se foi optado por unir op e quais e volta no log entrada_destinacao_tecido e atualiza
Responsável do Enfesto
Y
Responsável por input
Início do Enfesto
Z
Data de início ou de registro como início
Num de Rolos Enfestados
AA
Rolos enfestados informados no front
Se teve rolos bloqueados
AB
Rolos bloqueados informados no front
Motivos
AC
Motivos informados no front
Calculo de Rolos
AD
A diferença entre rolos recebidos na partida, rolos bloqueados e rolos enfestados
Número de Folhas
AE
Numero de folhas inputado pelo usuário ou lido automatico no risco 
Fim do Enfesto
AF
Data de finalizção do corte
Registro de finalização de enfesto
AG
Data de finalização do corte
Comprovante e Decisão- Tipo 3
AH
Exibe o resumo e a pessoa comprova
OPS em corte
AI
Mostra quais sao as OPs relacionadas
Inicio Corte
AJ
Início do corte
Grade
AK
Pega a grade no padrão: 3P/3M
Quantidade de Tamanhos
AL
Exibe a soma dos tamanhos da grade ex 12
Folhas
AM
quantidade de folhas que o usuário imputou ou que o sistema leu no risco
Retalhos?
AN
se houve retalho
Quantidade Cortada
AO
total somado automaticamente pelo calculo do front
Quantidade cortada por tamanho
AP
somado automaticamente pelo calculo no front 
Check de Recebimento
AQ
Recebimento de tecido na data x x x
folhas cortadas tamanho
AR
Deprecar
log de mudança
AS
Só para informar se houve ou nao juncao de op/corte
comprovante de decisão 5
AT
Registra o fim do corte
numero de volumes
AU
Dá pro usuário informar quantidade de vol
resumo dos volumes
AV
Exibe ao usuário como vai ficar a etiqueta dos volumes caso ele queira salvar, printar, imprimir. 
comprovante de decisão 6
AW
Se o usuário quis imprimir ou não e finaliza o processo. 



O paineConfeccao é um painel dedicado ao usuário externo Confecções> 
- Ele tem login com senha baseado na aba senhas_atuais, baseado no exemplo abaixo:



Confecção
Código
Senha Padrão
Antonio
AT
AntonioAT

Alimenta log_confeccoes:



Confecção Registro
A
Confecção que fez o login
Data de Acesso
B
Data do login
OPs Alocadas
C
OPs alocadas na confecção com base em entrada_destinacao_tecido
Produto
D
Produto alocado
Cor
E
Cor do produto alocado
Data Prevista
F
Previsão parte de data de fim do corte +10d e na ausência da data> estima pela data de envio do tecido +20d
PCs Estimadas
G
Quantidade de pcs estimadas de acordo com consumo por PC e KGs daquela OP
Valor Prévio de Pgto
H
A previsão de pagto de acordo com custo aba produto_consumo_custo
Qtd Cortada P
J
Destrincha e trás a quantidade cortada no P
Qtd Cortada M
K
Destrincha e trás a quantidade cortada no M
Qtd Cortada G
L
Destrincha e trás a quantidade no cortada no G
Qtd Cortada GG
M
Destrincha e trás a quantidade cortada no GG
Qtd Cortada XG
N
Destrincha e trás a quantidade cortada no XG
Total Cortado
O
Total cortado
Final do Corte
P
Data final do corte
Prévia de Pgto
Q
Prévia de pagto de acordo com a quantidade total cortada e o custo
NF- Remessa Industrialização
R
Numero da nota de remessa enviada/romaneio
Data Real Entrega Confecção
S
Data de entrega da costura
Agendamento de Envio
T
Data que agenda o envio da confecção
Data de Envio
U
Data de envio marcada pela confecção> retirada do motorista
Motorista
V
Motorista que fez a retirada na confecção
Data de Início Confecção
W
Data que a confecção recebeu 
Status Confecção
X
Status fixos> costura finalizada, costura iniciada, recebido na confecção
Qtd Costurada P
Y
Quantidade costurada e inputada pelo usuário para confrontar com corte
Qtd Costurada M
Z
Quantidade costurada e inputada pelo usuário para confrontar com corte
Qtd Costurada G
AA
Quantidade costurada e inputada pelo usuário para confrontar com corte
Qtd Costurada GG
AB
Quantidade costurada e inputada pelo usuário para confrontar com corte
Qtd Costurada XG
AC
Quantidade costurada e inputada pelo usuário para confrontar com corte
Total Costurado
AD
Quantidade costurada e inputada pelo usuário para confrontar com corte
Data finalização costura
AE
Data de finalização real da costura
Data de Agendamento Retirada Confecção
AF
Data que agendou a retirada
Data de Retirada Real Confecção
AG
Data real de retirada
Valor a Pagar Confecção
AH
Valor a pagar baseado na quantidade total costurada
Data de Vcto Confecção
AI
Do dia de envio +10d
NF- Retorno Industrializado
AG
NF de retorno enviada pela confecção
Motorista
AH
Motorista que retirou




A página de login com senha está em uso> funciona porém terá de haver alterações no layout> deixar mais responsivo e usual para mobile, porém adaptado para desktop evitando essa tela enorme e a falta de visualização da senha digitada> devemos disponibilizar uma forma do usuário habilitar a visualização de senha e também resetar a própria senha (gravando a escolha em senhas_atuais. 



Esse painel também está em uso e funcional, porém poderia ser mais inteligente se a costura já foi dada como finalizada> nem mostra ela nessa lista, podemos oferecer um dropdown para que ele escolha se deseja ver> OPs ainda não costuradas, recebidas e etc ou se deseja visualizar as que finalizou para fins de controle, download de csv e etc, ou até abrir direto uma planilha do google para aquele fornecedor ficar controlando as OPs dele por lá também. 



Depois que o usuário seleciona uma ação essa página se abre, pode ser mais inteligente se ela mostrar a quantidade cortada daquela OP por tamanho, assim já força o usuário a confrontar infos logo de início. 

As outras ações estão bem estruturadas. 

Ao finalizar a ação seja qual for precisamos sempre:
- Salvar a info em aba entrada_destinacao_tecido colunas AL e AM  com o status. 
- Salvar a info em log_confeccao 

Agora o painelEstoque:



Na tela de início do painel o objetivo é dar acesso a dash, mas também trazer automáticamente uma visão geral do estoque por isso Saldo atual: carregando… deveria nos mostrar o saldo total do estoque separando eles> Saldo estoque total lisas e Saldo total estoque estampadas. 

Mas conforme o usuário itera e informa um produto e uma cor> ele entende e adapta a visualização para o usuário conforme filtragem. 

O painel recebeu uma nova funcionalidade> a de classificar o tipo de estoque, para que sejamos extremamente cuidadosos com o que estamos movimentando interna/externa. 

Essa informação deve ser refletida em Log Estoque Total mas também na aba de origem que a trás:



Produto
A
Qual produto o usuário selecionou para movimentar
Cor
B
Qual cor o usuário escolheu movimentar de X produto
Tamanho
C
Qual tamanho o usuário escolheu movimentar
Estampa
D
Qual estampa> se tem ou se é liso.
Responsável
E
Quem está inputando
Origem
F
De onde saiu
Destino
G
Para onde vai
OP
H
OP 
Data
I
Dia da movimentação
Qtd Entrada
J
Qtd que entrou
Qtd Saída
K
Qtd que saiu
Tipo
L
Tipo de movimentação
SKU
M
QUAL SKU de lisa ou estampada
Saldo
N
Qual o saldo daquele dia/movimentação> o saldo sempre deve ser preenchido
Origem Registro
0
Qual a origem do registro
Ultima_ocorrencia
P
Se é a última ocorrencia do SKU
Classificação
Q
Qual classificação
SKU Transformado
R
Se o SKU saiu de lisa pra estampada ou já nasceu sendo estampado








Modo de input: Define se a pessoa vai usar peso como premissa ou se ela vai digitar direto e usar a calculadora para somar multiplos volumes:



Tipo de Movimentação: Define o fluxo de processos e o recálculo do saldo. 


Essas movimentações por natureza devem  cada uma provocar um tipo de recalculo no saldo como exemplificado acima. A contagem rotineira deve olhar para o saldo atual e para o saldo informado e se for aproximado> equilibra para equalizar de acordo com a contagem daquele destino. 

Essa informação deve ser salva no Log Estoque Total bem como cada movimentação ter uma aba para justificar e gravar realmente o retroativo/histórico. 

Log Estoque Total tem as seguintes colunas apresentadas acima, além dela temos que ter um log para cada tipo de movimento e a Log Estoque Total representando saldo de lisas e saldo estampada + transformação de SKU, ou seja o SKU nasceu liso e morre estampado por isso a troca, hoje temos uma aba chamada SKU_estampadas, a versão atual de SKU_estampadas contempla colunas de A a E:

A                          B                        C                         D                        
SKU
Produto
Estampa
Cor
Tamanho


Existindo uma aba chamada procv na estrutura retirada do site:


ID
A
Código identificador do site
SKU
B
Código identificador universal e oficial
DESCRIÇÃO
C
Descrição que contém info completa: produto, cor, estampa.
Produto
D
Nome do produto
URL IMAGEM 1
E
Imagem em link
Produto
F
Nome do produto
Estampa
G
Nome da estampa
TAMANHO
H
Tamanho do produto
COR
I
Cor do produto



Primeiro precisamos fazer com que essas duas informações cheguem uma para outra, ou seja que a info do site da aba procv, consiga ser compreendida pela aba SKU_estampadas, assim bebendo da fonte da aba procv para se alimentar e dar SKUs, essa seria aba de SKUs na verdade. Já no caso das peças que nascem (entram como lisas) a gente já dá um SKU pra cada de acordo com os sufixos do produto, cor e tamanho. 

Hoje é necessário que seja lido Log Estoque Total como sendo um transmissor de saldo daquela movimentação última de cada SKU. É importante que seja feito o cálculo conforme as premissas:

Se o tipo de movimentação for:
- Entrada- Pulmão: + X PCs em Pulmão 
- Destino: Imputa esse X somado ao  saldo de determinado destino> Suapé ou Montanaro.

- Saída- Pulmão: -X PCs em Pulmão
- Destino: Subtrai esse X como sendo > O que foi entrada (-) o que foi saída= saldo naquele destino. Na inexistência de saldo anterior ou havendo saldo negativo: deve equilibrar com esse input como sendo a fonte da verdade: é isso que tem. Há a mudança de SKU lisa para estampada,  ou seja significa não apenas a saída do X em saldo, mas a transformação do produto> que dá entrada naquele SKU de estampada.

- Entrada- Direto para estampar: +X PCs de Entrada no Pulmão de Lisas e X PCs transformadas para alimentar o saldo de estampadas com a troca oficial do SKU> o log evidencia a mudança.

- Contagem Rotineira: olha para o saldo atual em determinado destino e equilibra, se faltar> complementa a diferença e se sobrar da saída para equilibrar. 

Balanço: olha para o saldo atual e o ignora, assumindo aquele input de balanço como verdade. 

Sobre destinos:
 - Máquina de Silk/DTF: Representa na literalidade qual setor de estampa ficou responsável pelo produto liso para transformá-lo em estampado, só que de qualquer forma, também assume que o SKU daquela estampa receberá mais peças em estoque para o picking e terá de entender que houve aquela saída. 
 
Pulmão- Suapé: Evidência o que foi para esse galpão cinza, Suapé. 
Pulmão- Montanaro: Evidência o que foi para o galpão laranja, Montanaro. 
Pick And Packing: Representa o que foi para o estoque de estampadas e que foi para o cálculo de reserva no estoque. 



Aqui consiste a lógica futura que desejamos:

Junto com a mudança de galpão, haverá a troca de destinos, que ao invés de mencionar o destino físico da peça, como funcionaremos em um galpão só passará a ditar processos em termos de etapa, ou seja, ao invés de destino teríamos> etapas, que acompanhassem o ciclo de vida completo de um produto:
- Quando era programação
- Quando era projeção de demanda junto de metas de Growth 
- Quando virou romaneio e deu entrada junto das partidas
- Quantos rolos, KGs> por tecido, cor, produto e quantas PCs estimadas
- Quando o romaneio foi recebido no corte e se foi recebido em conformidade> OTIF. 
- Quando foi pra corte> o que virou, quanto de consumo deu, qual grade,, quantas pcs cortadas por grade e no total, quem cortou, quando cortou.
- Quando foi pra confecção> quem levou (logística)
- Quando chegou na confecção> estava em conformidade, quanto costurou, quanto foi 1a qualidade, quanto foi 2a qualidade, quando terminou, quanto custou, quando devemos pagar. 
- Quanto tem em cada confecção> qual status, desde quando, o que. 
- Quanto tem para chegar: quando será recebido, de quem, quanto, o que. 
- Quanto e como chegou> bateu com as infos da confecção, devemos mesmo pagar aquele valor, qual NQA. 
- Quando chegou> foi direto pra pulmão? foi direto pra estampar? qual maquina, qual equipe, quando, quanto. 
- Quando saiu> saiu de qual lugar? do pulmão de lisas que precisou estampar correndo? ja tinha em estoque de estampada? quando saiu, quanto, que dia, supriu as vendas?

Integrações:
O webapp deve se conectar com RFID, possibilitando a leitura inteligente das quantidades, ao mesmo tempo facilitando integração com sistemas externos de conferencia de pedidos errados, para maior automação e agilidade de Picking and Packing. 

Hoje o site não tem nenhuma conexão externa e isso dificulta a atuação:
- Estoque confuso: dois prédios tentam dividir por “igual” uma série de produtos/estampas/cores e tamanhos. Um dos estoques tem um capacity de aderir 17.7k PCs, nele funcionam 2 máquinas de silk, 2 de dobragem, uma sala de “conferência”, um salão pra Packing, uma sala de DTF, um estoque para reposição para cerca de 5k pcs, ou seja, nesse local há em média capacity de estocagem de 25k de produto (pensando no que tem guardado tb na sala de DTF e ao longo da empresa), os pedidos que chegam de devolução são todos  acumulados em sacos…. Que literalmente podem aguardar um SLA de 3,5 ou 45 dias e ninguém vai questionar, podendo haver ali uma série de produtos que sanariam algum pedido faltante e atual. 
Em ambos os prédios temos o padrão de prateleira nas paredes ao redor e gaiolas ou nichos de grade no meio, ontem também tenta-se distribuir melhor para a separação. 
No prédio da Montanaro acontece a separação: seria o first step do Picking and Packing, lá elas recebem os pedidos do dia seguinte no processo que ocorre como é (AS IS), depois elas casam as notas impressas (a nota do pedido com a nota de envio), o que também parece desnecessário e arcaico, cada uma pega um bolinho de pedidos em sua mesa e hoje os atores são: 


*Separação*: 
Stefhany
Maria Eduarda
Lucimara
Vitoria
Ana luíza
Ketty
Sabrina Vieira
Thayna
Juliana > 9 Pessoas

*Conferencia*
Heloisa(Gravida)
Camila(Gravida e afastada)
Sabrina feijó(Gravida)
Gabriella Cristine (Gravida)
Sabrina Stefany(Gravida)> 5 Pessoas


*Embalagem e outros*:
Karina
Dani
Jackline
Cristiane/ encarregada
Gustavo
Novo funcionário  > 6 pessoas 

Total=20  pessoas


O processo que starta na separação- Atual prédio Montanaro (um em frente ao outro), futuro prédio unificado, ou seja setores em conjunto 
Starta assim: 
Recebe as notas pela manhã 
Stefanny casa manualmente as notas para o time e distribui nas mesas 
Cada mesa vai até as gôndolas/nicho e se serve e se faltar pega o rádio e chama reposição para o apoio do outro prédio que vai com carrinho até o local, repõe e leva
Os pedidos que não puderam ser completos: são devolvidos na gôndola (retrabalho, se não havia e temos essa informação - pois estamos atualmente contando estoque e colocando isso no sistema) era só já não imprimir isso para o picking. 
Esses pedidos são separados, colocados num saquinho junto de suas notas casadas, enviados pelo carrinho até o setor de conferência, onde se inicia a conferência de se os tamanhos e estampas estão corretos com o pedido na nota, ou se houve algum erro, tendo erro: repõe se der e se não der envia de volta pro setor da Montanaro fazer a troca, nisso também conferem se há linhas sobrando ou algum defeito gritante. 
Amarram os saquinhos e põe num carrinho que vai até a mesa de embalamento, onde o packer abre o saco ( contando já fecharam e abriram o saco 3x) e colam do lado de fora a etiqueta e acumulam pra chegada do correio. 
Na prática: isso se acumula em várias etapas, acumulam-se pedidos sem separação completa, mas dá retrabalho pro Picker, ao mesmo tempo complica o Picker que tem Leg Day P em mais de 2 , 3, 4 ou 5 lugares na empresa, então ele fica indo e vindo ou esperando alguém repor. E aí na hora de embalar vai periquito e papagaio, todo mundo embala, até pessoas da dobragem, pessoas de outros setores. E o máximo de pedidos já enviados nesse modelo foram 1700 pedidos, nunca atingimos a marca de 2k pedidos. 
Começamos pela cronoanalise do processo, descrito ⬇️ 



Cronoanalise de Processos 
Processo de embalamento: 
9 segundos por Peça 
3 pessoas embalam 7 peças por minuto
(Cerca 3k pcs dia meta- realidade 2k peças) 
9 seg pc 
Processo de conferência:
4 por minuto 
2 pedidos 
2 pedidos  
26 segundos por pedido embalamento 
Média de 4 peças por minuto com duas pessoas 
processo de separação: 
1,06 min e 4 pedidos separados: em 3 pessoas, 30 segundos por pedido. 
30 seg 
processo de dobragem: 
1 pessoa só, 2min55 para um volume separar 
Em 1 min se dobrou 17 pcs método tradicional 
Em 1 min e 23 seg de 3/3 se dobrou 15 pcs 
As tonalidades de manga e gola são frequentes e atrapalham o trabalho da dobragem 
Faltam 55 sacos para dobrar, com média de 100 pcs saco, cerca de 5.5k (
Falta a senha de Adm da máquina nova e uma orientação técnica sobre as funções das máquinas antigas, trocar as placas laterais da primeira máquina de dobra. 
Uma pessoa iniciante e sem experiência dobra em 1 min cerca de 7 pcs na primeira tentativa. 
Soma do tempo produtivo: 1 minuto e 46 segundos por peça o processo inteiro executado por em média 3 pessoas ao mesmo tempo. 
Pensando na média de venda de  70k peças, num mix de produtos que disputam receita, mas tem protagonismo específico em Oversized sendo o boi de piranha. 
Hoje trabalham na dobragem com máquina automática 3 pessoas
Funcionamos em três prédios um em frente ao outro onde fazemos a silk, dobragem, separação, conferência, embalamento e expedição. Em outro prédio funciona o recebimento de tecido, enfesto, corte e distribuição para confecções que costuram e retornam o produto. 
As métricas acima são uma PoP para que a gente possa analisar com cronoanalise exemplos isolados que deem dimensão da capacidade produtiva dia, o total de funcionários que executam essa tarefa de separação, conferência, embalamento é de cerca de 15 pessoas, sendo 5 gestantes. 
A PoP futura seria dissipação de setores para criação de silos, ao invés de deixar um prédio separando, carrinhos atravessando e levando o que foi separado para conferência, indo pra um mesão e sendo embalado abrindo o saco que foi amarrado e fechando e etiquetando o pacote.
Pensei numa PoP que otimizasse espaço, ajudasse a dirimir panelinhas, unisse o time desfazendo a sensação de “não entrego minha parte porque setor tal não faz a dele”, dissipando os silos e criando uma colaboração que otimize a entrega e traga pertencimento. 
Então pensei em alguns passos: 
Há dois estoques, um em cada prédio, mas com praticamente os mesmos produtos que podem ser mapeados em www.berzerk.com.br, no fim do dia ou em vários momentos do dia várias pessoas saem de seus postos pra ajudar a embalar, é embalado, jogado no chão e aí o correio chega e várias pessoas precisam ir ajudando a jogar os pacotes dentro do caminhão. 
Esse seria o AS IS macro. Mas aí vem os pormenores, as meninas da conferência em tese deveriam somente conferir se foi separado corretamente pela separação, checando a etiqueta que tá dentro do saco, mas antes disso Stefane fica responsável no início do dia de casar as etiquetas de identificação do pacote e a de declaração do produto, o que toma 40min média, pela yampi deve haver uma forma de imprimir casado. 
Depois disso distribui-se de forma aleatoria nas mesas que ficam responsáveis por separar, colocar no saco, e colocar as duas etiquetas casadas dentro do saco, amarrar ou zipar (tá fora de padrão os sacos pra diminuir custo momentaneamente), amarram pra não soltar no carrinho. 
Esse cortinho atravessa a rua e chega lá no outro galpão, ou pode atravessar o próprio galpão, ha o movimento de carrinhos para levar essas separações para as conferentes, as conferentes abrem esse saco, checam se é o do mesmo tamanho/estampa e depois disso elas confirmam com caneta no próprio papel, se necessário reparam pequenos problemas de acabamento e liberam para o embalamento. 
O embalamento recebe tudo em carrinhos e vai jogando em cima de uma mesa grande com todos os pedidos, cada um coloca no saco e cola as etiquetas do lado de fora, muitas vezes tendo que abrir o saco pra pegar a etiqueta, ou abrindo o saco de alguma forma pra tirar a etiqueta e poder colar no pacote, finalizado esse processo, jogam no chão formando pilhas gigantes (média 2k pedidos dia) e aí vai pro correio, jogando saco a saco pra dentro do caminhão em coletivo. 
Sendo que 2k é um número comemorado, frente a demanda prevista de 70k pcs vendida mês, ainda estaremos cerca de 500 pcs abaixo da necessidade diária, operando com cerca de 15 pessoas dedicadas a tarefa. 
Pensando em 1min 46 seg para ter o processo completo pronto, pensei na dissipação do setor e na criação de grupos foçados na entrega completa: 
 Uma picker: responsável por pegar as peças que devem ser separadas 
Uma checker: que recebe as peças separadas e vai casando com suas respetivas etiquetas/completando o pedido 
Uma packer: que embala e identifica. 
Na mesma mesma: 
Suponhamos que temos ao todo 1 hora e meia não util, dando 6,7h úteis: 
As pickers fazem 30seg por pedido, hoje a disposição física delas é de araras cada arara contempla uma estampa, na sequência do P ao XG, mas a impressão que tive hoje é de que posso andar que nem barata tonta sem otimização nenhuma, se já sabe-se quais pedidos no dia; seria muito mais fácil talvez priorizar tamanho, sequência de estampa: todo P junto, Todo M junto, mas sempre na mesma sequência. O corredor com placa de identificação ALTA e clara, talvez faixas noren vindo do teto com uma seta gigante que evidencia o que está ali (tipo supermercado) ou uma placa alta que fique em cada arara, marcando o corredor. 
Talvez otimizar a leitura do que vem do yampi, primeiro passar a casar as etiquetas, depois passar a dar o pedido aos pickers melhor direcionado, ao invés de ficar perdendo tempo lendo cada etiqueta e voltando 30x no mesmo lugar, ela já pode receber uma lista clara no exemplo: 
Separação do dia X/X: 
Corredor A-C (OVERZIZED):   Oversized Caqui- Mithy (P) - 30 PCs
Corredor A-P (OVERSIZED) Oversized Preta- LegDay (90). 
NO FUTURO galpão, onde estaremos dentro dos próximos 60d a ideia é termos carrinhos com as estampas, carrinhos dos quais acomodam cerca de 750-800 pcs cada, então também teríamos de ter noção: quantos carrinhos seria necessário para acomodar peças lisas, quantos para peças estampadas. 


Pensando em 6,7h e 30 seg peça, imaginando que teríamos uma melhoria de 30% no tempo, diminuindo de 30seg pra 20seg pc, (402 min útil): 
2010 pcs separadas dia. 
Essas 2010 pcs vão pra checker: que hoje demora 26 seg para embalar e passaria a suponhamos, separar em 20seg: 2010 pcs também.
Embalamento que é 09seg, terminaria então mais cedo, o que hoje é energargaldo. Para checar aos 2500 e ainda oferecer uma meta de 5000 pcs dia, podemos fazer PoP com plano de ação focado em separar as 3 piores, fazer o teste de ciclo contínuo, verificar quantas peças separadas no dia, equiparando a 3 pessoas que fazem o processo ÀS IS. 
Quais resultados teríamos de produtivo, além disso facilitar a vida dessas meninas já com essa lista e essa reorganização de estoque. 
A PoP iniciou dia 12/06 com os pedidos de 12/06, 299 pedidos dispostos nesta planilha https://docs.google.com/spreadsheets/d/16LP_0Jm8vw_pBcbaNdpQlD34QgZ8j5aHy2WQO50ILSA/edit?usp=drivesdk, os pedidos referidos estão compiladas para testar V1. 
Em 10 min separamos todos os produtos P em duas pessoas, com as araras como estão, são cerca de 20 nichos como esse que cabem 50 PCs em média, temos prateleira ao longo de toda a parede, esses nichos/prateleiras são formados por 3 colunas e 5 células: =5*3*20‎ = 300 nichos de 50 pcs (300*50=15.000 
Com as da parede: 5k.
Cerca de 20/30k PCs cabem nesse espaço se ele estiver todo preenchido, Montanaro. 
Hoje temos dois galpões, com os mesmos produtos e muitas vezes o produto replicado em várias araras, quem separa da uma breve conferida, casa as etiquetas com os sacos, botam num carrinho e vai pra outro galpão, lá confere, essa conferência demora, em um dia um time de 20 pessoas emite 2k pedidos… muitas vezes tirando outras pessoas de suas funções pra embalar. 
Amanhã a POP trataria da P, M, G, GG, XG, p já foi separado, aí a ideia seria; 
Todo mundo checar a M, uma embalar. Depois todo mundo pegar e checar a M, todo mundo embalar, todo mundo pegar G, duas checar, uma embalar. 
Enfim, várias possibilidades. O objetivo é chegar em 2k pcs nos 420 min úteis dia com equipes pequenas, ao invés de silos células. 

O objetivo atual é de que 2K pcs sejam separados dia no mínimo, mas que tenhamos uma equipe enxuta com a ajuda da tecnologia dobrarmos isso, ou seja, termos capacity e hability para cuidar do dobro da meta com o mesmo time. 


No futuro bem próximo: os painéis órbitta precisam transmitir todo esse fluxo de processos, desde a programação até a saída que um picker vai dar, ou seja, história completa. Para controle financeiro, para projeções, para criação de rituais de alocação, mudança de cultura interna e de visão focada em dados. Tirar a Berzerk do fog of war, e trazer mais próxima de um sunny day. 


Já temos a conexão ativa com o tiny através da API, agora precisamos garantir que vamos conseguir:
- Utilizar nosso sistema e o saldo dos estoques para presumir: vendas do dia> quais devem ser impressas? quais devem aguardar? as que vão aguardar, aguardam até quando?
- O time atual: e se todos passarem ao invés de receber as notinhas, receberem direto>

“Picking Berzerk: 22/06/25. Hoje vocês devem separar:

Oversized Preta
Leg Day> 56 P, 87M, 97G, 98GG, 32XG> Confirmando a separação ou dando falta e informando se tem 0 ou se tem menos do que deveria. 

Shorts sem Compressão- Azul Marinho:
Logo- Azul Marinho: 32P, 53M

e assim por diante, ou seja> mostra o que foi vendido, mas só mostra se der pra separar pedidos completos. Só os completos.

(O próprio sistema passaria então a aderir ao que o usuário informou e recalcular rota> entender então quais pedidos não poderão ser separados e já avisa-lo que houve alterações inesperadas pela falta de produto não sinalizada no sistema anteriormente). 


Até que integre com RFID. 
Momento atual: migrando para lovable, só falta dar uma injeção de dados reais (que temos no sheets e devem alimentar o supabase para ter registros reais já imputados no sistema. 


Iniciando a apresentação dos códigos que hoje comandam o webapp:

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>📅 Entrada de Tecido - Berzerk</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 font-poppins min-h-screen p-6">
  <form id="entradaTecidoForm" class="bg-white shadow-md rounded-xl p-8 w-full max-w-6xl mx-auto space-y-8">
    <h1 class="text-3xl font-bold text-center mb-8">📅 Registrar Entrada de Tecido</h1>

    <!-- 1. Contexto Inicial -->
    <div class="bg-gray-200 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">1⃣ Contexto Inicial</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <select id="tipoEntrada" class="border rounded-lg p-2 w-full" required>
          <option value="">Selecione Tipo de Entrada</option>
          <option value="Programada">Programada</option>
          <option value="Não Programada">Não Programada</option>
        </select>
        <select id="produto" onchange="carregarTecidos()" class="border rounded-lg p-2 w-full" required></select>
        <select id="malharia" class="border rounded-lg p-2 w-full" required></select>
        <select id="cor" class="border rounded-lg p-2 w-full" required></select>
        <input type="text" id="romaneio" placeholder="Romaneio/NF" class="border rounded-lg p-2 w-full" required>
        <input type="date" id="dataEnvio" class="border rounded-lg p-2 w-full" required>
        <select id="responsavel" class="border rounded-lg p-2 w-full" required>
          <option value="">Selecione Responsável</option>
          <option value="Dai">Dai</option>
          <option value="Kado">Kado</option>
          <option value="Outro">Outro</option>
        </select>
        <input type="number" id="numPartidas" min="1" value="1" placeholder="Número de Partidas" class="border rounded-lg p-2 w-full">
      </div>
    </div>

    <!-- 2. Tecidos Relacionados -->
    <div class="bg-gray-300 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">2⃣ Tecidos Relacionados</h2>
      <div id="areaTecidos" class="space-y-6"></div>
      <input type="hidden" id="tecido" value="">
    </div>

    <!-- 3. Resumo do Pedido -->
    <div class="bg-green-100 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">3⃣ 📈 Resumo do Pedido</h2>
      <div id="resumoCalculos" class="grid grid-cols-1 md:grid-cols-2 gap-4 text-gray-700 font-semibold">
        <div><strong>PCS Estimadas:</strong> <span id="pcsEstimadas">0</span></div>
        <div><strong>Total KG:</strong> <span id="totalKg">0</span></div>
        <div><strong>Total Rolos:</strong> <span id="totalRolos">0</span></div>
        <div><strong>Valor Total s/ Viés:</strong> R$ <span id="valorTotalSemVies">0.00</span></div>
        <div><strong>KG Viés:</strong> <span id="kgVies">0</span></div>
        <div><strong>Rolos Viés:</strong> <span id="rolosVies">0</span></div>
        <div><strong>Valor Viés:</strong> R$ <span id="valorVies">0.00</span></div>
        <div><strong>Valor Final:</strong> R$ <span id="valorFinal">0.00</span></div>
        <div class="col-span-2"><strong>Data de Vencimento:</strong> <span id="dataVencimento">--/--/----</span></div>
      </div>
    </div>

    <!-- 4. Status da Ribana -->
    <div class="bg-green-300 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">⚠️ Status da Ribana</h2>
      <div id="statusRibana" class="text-xl font-bold"></div>
    </div>

    <!-- 5. Dimensão de Partidas -->
    <div id="dimensaoPartidas" class="bg-yellow-200 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">📦 Dimensão de Partidas</h2>
      <div id="listaPartidas" class="space-y-4"></div>
    </div>

    <!-- 6. Cortes e OPs -->
    <div class="bg-yellow-100 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">✂️ Cortes e Geração de OPs</h2>
      <div id="numeroCortes" class="text-lg mb-4 font-semibold text-gray-800"></div>
      <div id="opsGeradas" class="space-y-2"></div>
    </div>

    <!-- 7. Destino do Tecido -->
    <div class="bg-blue-100 p-6 rounded-xl">
      <h2 class="text-2xl font-bold mb-4">🚺 Destino do Tecido</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <select id="cortador" class="border rounded-lg p-2 w-full" required>
          <option value="">Selecione Cortador</option>
        </select>
      </div>
    </div>

    <!-- Botão -->
    <div class="flex justify-center">
      <button id="registrarBtn" type="button" onclick="processarEntrada()" disabled class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-4 px-8 rounded-xl transition-all opacity-50 cursor-not-allowed">
        ✅ Registrar Entrada
      </button>
    </div>
  </form>

  <footer class="text-xs text-gray-400 mt-12 text-center">
    Sistema Berzerk © Orbitta 2025
  </footer>
<!-- Scripts embutidos no final -->
<script>

// ======================================================================
// 🚀 1. Inicialização automática ao carregar o painel
// ======================================================================

window.addEventListener('load', () => {
  // 🔽 Carrega dados de dropdowns ao abrir o painel
  google.script.run
    .withSuccessHandler(popularDropdowns)
    .withFailureHandler(err => {
      console.error("🔥 ERRO no carregamento dos dropdowns:", err.message);
      alert("Erro ao carregar os dropdowns. Verifique se as abas e colunas estão certas.");
    })
    .getDropDown();

  // 🔁 Escuta alterações no campo de número de partidas
  const numPartidasInput = document.getElementById('numPartidas');
  if (numPartidasInput) {
    numPartidasInput.addEventListener('input', renderizarPartidas);
    renderizarPartidas(); // Garante que 1 partida seja mostrada inicialmente
  }
});


// ======================================================================
// 📥 2. Dropdowns (Produto, Cor, Malharia, Cortador, etc.)
// ======================================================================

function popularDropdowns(dados) {
  preencherSelect('produto', dados.produtos, 'Selecione o Produto');
  preencherSelect('malharia', dados.malharias, 'Selecione a Malharia');
  preencherSelect('cor', dados.cores, 'Selecione a Cor');
  if (document.getElementById('cortador')) preencherSelect('cortador', dados.cortadores, 'Selecionar Cortador');
  if (document.getElementById('destinoConf')) preencherSelect('destinoConf', dados.confecções, 'Selecionar Confecção Destino');
  window.listaConfecções = dados.confecções || []; // usado em renderização de OPs
}

function preencherSelect(id, opcoes, placeholderText) {
  const select = document.getElementById(id);
  if (!select) return;
  select.innerHTML = `<option value="">${placeholderText}</option>`;
  opcoes?.forEach(opcao => {
    const opt = document.createElement('option');
    opt.value = opt.textContent = opcao.trim();
    select.appendChild(opt);
  });
}


// ======================================================================
// 🧵 3. Tecidos relacionados ao produto selecionado
// ======================================================================

function carregarTecidos() {
  const produto = document.getElementById('produto').value;
  if (!produto) return;
  google.script.run.withSuccessHandler(renderizarTecidos).getTecidosDoProduto(produto);
}

function renderizarTecidos(tecidos) {
  const container = document.getElementById('areaTecidos');
  container.innerHTML = '';
  if (tecidos.principal) criarCampoTecido('principal', tecidos.principal, true);
  if (tecidos.complementar) criarCampoTecido('complementar', tecidos.complementar, false);
  if (tecidos.aviamento) criarCampoTecido('aviamento', tecidos.aviamento, false);
  document.getElementById('tecido').value = tecidos.principal || '';

  // 🔁 Escuta alterações nos inputs para recalcular resumo
  document.querySelectorAll('input[type="number"]').forEach(input =>
    input.addEventListener('input', prepararCalculoResumo)
  );

  gerarCortesEOPs(); // tenta gerar OPs logo após carregamento inicial de tecidos
}

function criarCampoTecido(tipo, nome, obrigatorio) {
  const div = document.createElement('div');
  div.className = 'grid grid-cols-1 md:grid-cols-3 gap-4';
  div.innerHTML = `
    <div class="col-span-1">
      <label class="font-semibold">${tipo.toUpperCase()} - ${nome}</label>
    </div>
    <input type="number" id="kg_${tipo}" class="border rounded-lg p-2 w-full" placeholder="KG de ${nome}" ${obrigatorio ? 'required' : ''}>
    <input type="number" id="rolos_${tipo}" class="border rounded-lg p-2 w-full" placeholder="Rolos de ${nome}">
  `;
  document.getElementById('areaTecidos').appendChild(div);
}


// ======================================================================
// 📦 4. Partidas - renderização e escuta de rolos
// ======================================================================

function renderizarPartidas() {
  const container = document.getElementById('listaPartidas');
  container.innerHTML = '';
  const numPartidas = parseInt(document.getElementById('numPartidas')?.value || 0);

  for (let i = 1; i <= numPartidas; i++) {
    container.innerHTML += `
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <input id="partidaId_${i}" placeholder="ID da Partida ${i}" class="border rounded-lg p-2 w-full" />
        <input id="rolosPartida_${i}" placeholder="Rolos" type="number" class="border rounded-lg p-2 w-full" oninput="calcularCortesPartida(${i})" />
        <div id="resumoPartida_${i}" class="text-gray-700 font-semibold"></div>
      </div>`;
  }

  gerarCortesEOPs(); // dispara tentativa de geração logo após renderizar campos
}

function calcularCortesPartida(partidaIndex) {
  const rolos = parseInt(document.getElementById(`rolosPartida_${partidaIndex}`)?.value || 0);
  const produto = document.getElementById('produto')?.value;
  if (!produto || !rolos) return;

  google.script.run.withSuccessHandler((rolosMax) => {
    const cortes = rolosMax && rolosMax > 0 ? Math.ceil(rolos / rolosMax) : 1;
    document.getElementById(`resumoPartida_${partidaIndex}`).innerText =
      `🔪 ${rolos} rolos ➜ ${cortes} cortes`;
    gerarCortesEOPs();
  }).buscarRolosMaximosPorCorte(produto);
}


// ======================================================================
// ✂️ 5. Geração de Cortes e OPs
// ======================================================================

let mapaOpsPorPartida = {};
let contadorNaoAlocado = 1;

function gerarCortesEOPs() {
  const produto = document.getElementById('produto').value;
  const cor = document.getElementById('cor').value;
  const tecido = document.getElementById('tecido').value;
  const dataEnvio = document.getElementById('dataEnvio').value;
  const numPartidas = parseInt(document.getElementById('numPartidas')?.value || 0);
  const idEntrada = `ENTRADA-${crypto.randomUUID().slice(0, 8).toUpperCase()}`;

  if (!produto || !tecido || !cor || !dataEnvio || !numPartidas) return;

  mapaOpsPorPartida = {};
  const promessas = [];

  for (let i = 1; i <= numPartidas; i++) {
    const partidaId = document.getElementById(`partidaId_${i}`)?.value || `P${i}`;
    const rolos = parseInt(document.getElementById(`rolosPartida_${i}`)?.value || 0);
    if (!rolos || rolos <= 0) continue;

    const confecSelect = document.getElementById(`confOp_${i - 1}`);
    const confecNome = confecSelect?.value || "";
    let codFornecedor = confecNome ? null : `NA${contadorNaoAlocado++}`;

    const p = new Promise((resolve) => {
      if (confecNome) {
        google.script.run.withSuccessHandler((codigo) => {
          codFornecedor = codigo || "NA0";
          gerarOPsInterno();
        }).buscarCodigoFornecedor(confecNome);
      } else {
        gerarOPsInterno();
      }

      function gerarOPsInterno() {
        google.script.run.withSuccessHandler((rolosMax) => {
          const cortes = rolosMax && rolosMax > 0 ? Math.ceil(rolos / rolosMax) : 1;
          const ops = [];

          for (let j = 1; j <= cortes; j++) {
            ops.push(gerarOPCompleta({
              tecido,
              cor,
              idEntrada,
              codFornecedor,
              partidaId,
              indexCorte: j,
              totalCortes: cortes
            }));
          }

          mapaOpsPorPartida[partidaId] = ops;
          resolve();
        }).buscarRolosMaximosPorCorte(produto);
      }
    });

    promessas.push(p);
  }

  Promise.all(promessas).then(() => {
    renderizarOPsGeradas();
  });
}



function gerarOPCompleta({ tecido, cor, idEntrada, codFornecedor, partidaId, indexCorte, totalCortes }) {
  const hoje = new Date();
  const mes = hoje.getMonth() + 1;

  const extrairConsoantes = (texto, n = 2) =>
    (texto || "")
      .toUpperCase()
      .normalize("NFD")
      .replace(/[AEIOU\s\u0300-\u036f]/g, '')
      .slice(0, n) || "XX";

  const consoanteTecido = extrairConsoantes(tecido, 1);
  const consoantesCor = extrairConsoantes(cor, 2);
  const sufixoEntrada = idEntrada ? (idEntrada.match(/.{3}$/) || ['000'])[0] : '000';

  return `OP${mes}${consoanteTecido}${consoantesCor}${sufixoEntrada}-${codFornecedor}-${partidaId}-${indexCorte}/${totalCortes}`;
}


function renderizarOPsGeradas() {
  const container = document.getElementById('opsGeradas');
  container.innerHTML = '';

  let totalOps = 0;

  Object.entries(mapaOpsPorPartida).forEach(([partidaId, ops]) => {
    ops.forEach((op, index) => {
      const div = document.createElement('div');
      div.className = 'bg-white border p-4 rounded-xl shadow-md mb-2 flex justify-between items-center';
      div.innerHTML = `
        <span class="font-semibold">${op}</span>
        <select class="border rounded-lg p-2 w-1/2" id="confOp_${totalOps}">
          <option value="">Selecione Confecção</option>
        </select>
      `;
      container.appendChild(div);

      const select = document.getElementById(`confOp_${totalOps}`);
      if (window.listaConfecções && Array.isArray(window.listaConfecções)) {
        window.listaConfecções.forEach(conf => {
          const opt = document.createElement('option');
          opt.value = opt.textContent = conf.trim();
          select.appendChild(opt);
        });
      }

      totalOps++;
    });
  });

  if (totalOps === 0) {
    container.innerHTML = `<div class="text-red-500 font-bold">❌ Nenhuma OP gerada.`;
  }
}



// ======================================================================
// 📊 6. Cálculo de resumo de pedido (quantidades, valores, ribana, etc.)
// ======================================================================

function prepararCalculoResumo() {
  const kgPrincipal = parseFloat(document.getElementById('kg_principal')?.value) || 0;
  const kgComplementar = parseFloat(document.getElementById('kg_complementar')?.value) || 0;
  const kgAviamento = parseFloat(document.getElementById('kg_aviamento')?.value) || 0;
  const kgRibana = parseFloat(document.getElementById('kg_ribana')?.value) || 0;

  const rolosPrincipal = parseFloat(document.getElementById('rolos_principal')?.value) || 0;
  const rolosComplementar = parseFloat(document.getElementById('rolos_complementar')?.value) || 0;
  const rolosAviamento = parseFloat(document.getElementById('rolos_aviamento')?.value) || 0;
  const rolosRibana = parseFloat(document.getElementById('rolos_ribana')?.value) || 0;

  const totalKg = kgPrincipal + kgComplementar + kgAviamento + kgRibana;
  const totalRolos = rolosPrincipal + rolosComplementar + rolosAviamento + rolosRibana;

  const produto = document.getElementById('produto').value;
  const malharia = document.getElementById('malharia').value;
  if (!produto || !malharia) return;

  google.script.run.withSuccessHandler(function(info) {
    if (!info) {
      alert("❌ Produto não encontrado na base!");
      return;
    }

    const consumoMedio = parseFloat(info.consumoPorPc) || 0;
    const valorKgPrincipal = parseFloat(info.valorKgPrincipal) || 0;

    const pcsEstimadas = consumoMedio > 0 ? Math.floor(kgPrincipal / consumoMedio) : 0;
    const valorPrincipal = kgPrincipal * valorKgPrincipal;
    const valorTotalSemVies = valorPrincipal;

    const consumoViesPorPc = 0.004;
    const valorViesUnitario = 0.35;
    const kgVies = pcsEstimadas * consumoViesPorPc;
    const rolosVies = Math.ceil(kgVies / 18);
    const valorVies = pcsEstimadas * valorViesUnitario;
    const valorFinal = valorTotalSemVies + valorVies;

   const necessarioRibana = kgPrincipal * 0.05;
   const margemTolerancia = 0.01;
   const ribanaOk = (kgRibana + margemTolerancia) >= necessarioRibana;

   const statusRibana = ribanaOk
   ? `✅ Ribana OK`
   : `⚠️ Ribana Insuficiente - Solicitar mais ${(necessarioRibana - kgRibana).toFixed(2)} kg`;

   document.getElementById('statusRibana').innerText = statusRibana;


    const dadosResumo = {
      pcsEstimadas,
      totalKg,
      totalRolos,
      valorTotalSemVies,
      kgVies,
      rolosVies,
      valorVies,
      valorFinal,
      dataVencimento: new Date(Date.now() + 10 * 86400000) // 10 dias após hoje
    };

    calcularResumo(dadosResumo);
    gerarCortesEOPs(); // importante: atualiza as OPs com base nos tecidos
    validarCampos();
  }).buscarDadosProdutoCompleto(produto, malharia);
}

function calcularResumo(resumo) {
  document.getElementById("pcsEstimadas").innerText = resumo.pcsEstimadas;
  document.getElementById("totalKg").innerText = resumo.totalKg;
  document.getElementById("totalRolos").innerText = resumo.totalRolos;
  document.getElementById("valorTotalSemVies").innerText = resumo.valorTotalSemVies.toFixed(2);
  document.getElementById("kgVies").innerText = resumo.kgVies.toFixed(2);
  document.getElementById("rolosVies").innerText = resumo.rolosVies;
  document.getElementById("valorVies").innerText = resumo.valorVies.toFixed(2);
  document.getElementById("valorFinal").innerText = resumo.valorFinal.toFixed(2);
  document.getElementById("dataVencimento").innerText = new Date(resumo.dataVencimento).toLocaleDateString("pt-BR");
}


// ======================================================================
// ✅ 7. Validação de Campos Obrigatórios antes de habilitar o botão "Registrar"
// ======================================================================

function validarCampos() {
  // Lista dos campos mínimos que devem estar preenchidos para liberar o botão
  const camposObrigatorios = [
    'tipoEntrada', 'produto', 'malharia', 'cor',
    'romaneio', 'dataEnvio', 'responsavel', 'kg_principal'
  ];
  
  // Verifica se todos os campos estão preenchidos
  const completo = camposObrigatorios.every(id => {
    const el = document.getElementById(id);
    return el && el.value && el.value.trim() !== '';
  });

  // Atualiza o estado do botão com base nessa validação
  const botao = document.getElementById('registrarBtn');
  botao.disabled = !completo;
  botao.classList.toggle('opacity-50', !completo);
  botao.classList.toggle('cursor-not-allowed', !completo);
}


// ======================================================================
// 📤 8. Coleta de Dados para Envio ao Backend
// ======================================================================

function coletarDados() {
  const confecçõesPorOP = [];
  const numPartidas = parseInt(document.getElementById('numPartidas')?.value || 0);
  const partidas = [];
  let contadorGlobal = 0; // 🚨 Contador fixo para confOp_N

  for (let i = 1; i <= numPartidas; i++) {
    const partidaId = document.getElementById(`partidaId_${i}`)?.value || `P${i}`;
    const rolos = parseInt(document.getElementById(`rolosPartida_${i}`)?.value || 0);
    if (!rolos || isNaN(rolos) || rolos <= 0) continue;

    partidas.push({ id: partidaId, rolos });

    const opsDaPartida = mapaOpsPorPartida[partidaId] || [];

    for (let j = 0; j < opsDaPartida.length; j++) {
      const op = opsDaPartida[j];
      const select = document.getElementById(`confOp_${contadorGlobal}`);
      const confSelecionada = select ? select.value : "";

      confecçõesPorOP.push({
        op: op,
        confeccao: confSelecionada,
        partidaId,
        indexCorte: j + 1,
        totalCortes: opsDaPartida.length
      });

      contadorGlobal++; // 🔁 avança pra próxima confOp_X
    }
  }

  return {
    tipoEntrada: document.getElementById('tipoEntrada')?.value || '',
    produto: document.getElementById('produto')?.value || '',
    malharia: document.getElementById('malharia')?.value || '',
    cor: document.getElementById('cor')?.value || '',
    tecido: document.getElementById('tecido')?.value || '',
    romaneio: document.getElementById('romaneio')?.value || '',
    dataEnvio: document.getElementById('dataEnvio')?.value || '',
    responsavel: document.getElementById('responsavel')?.value || '',
    kgPrincipal: parseFloat(document.getElementById('kg_principal')?.value) || 0,
    rolosPrincipal: parseInt(document.getElementById('rolos_principal')?.value) || 0,
    kgComplementar: parseFloat(document.getElementById('kg_complementar')?.value) || 0,
    rolosComplementar: parseInt(document.getElementById('rolos_complementar')?.value) || 0,
    kgAviamento: parseFloat(document.getElementById('kg_aviamento')?.value) || 0,
    rolosAviamento: parseInt(document.getElementById('rolos_aviamento')?.value) || 0,
    kgRibana: parseFloat(document.getElementById('kg_ribana')?.value) || 0,
    rolosRibana: parseInt(document.getElementById('rolos_ribana')?.value) || 0,
    pcsEstimadas: parseInt(document.getElementById('pcsEstimadas')?.innerText) || 0,
    totalKg: parseFloat(document.getElementById('totalKg')?.innerText) || 0,
    totalRolos: parseInt(document.getElementById('totalRolos')?.innerText) || 0,
    valorTotalSemVies: parseFloat(document.getElementById('valorTotalSemVies')?.innerText.replace(/[^\d,.-]/g, '').replace(',', '.')) || 0,
    kgVies: parseFloat(document.getElementById('kgVies')?.innerText) || 0,
    rolosVies: parseInt(document.getElementById('rolosVies')?.innerText) || 0,
    valorVies: parseFloat(document.getElementById('valorVies')?.innerText.replace(/[^\d,.-]/g, '').replace(',', '.')) || 0,
    valorFinal: parseFloat(document.getElementById('valorFinal')?.innerText.replace(/[^\d,.-]/g, '').replace(',', '.')) || 0,
    dataVencimento: document.getElementById('dataVencimento')?.innerText || '',
    statusRibana: document.getElementById('statusRibana')?.innerText || '',
    cortador: document.getElementById('cortador')?.value || '',
    opDestinoList: confecçõesPorOP,
    partidas: partidas
  };
}



// ======================================================================
// 💾 9. Registro da Entrada Final (função final de envio ao backend)
// ======================================================================

function processarEntrada() {
  const dados = coletarDados();

  google.script.run
    .withSuccessHandler(() => {
      alert("✅ Entrada registrada com sucesso!");

      const botao = document.getElementById('registrarBtn');
      botao.textContent = "✅ Entrada Registrada!";
      setTimeout(() => {
        botao.textContent = "✅ Registrar Entrada";
      }, 2000);

      // 🧹 Limpa todos os campos visuais
      document.getElementById('entradaTecidoForm').reset();
      document.getElementById('areaTecidos').innerHTML = '';
      document.getElementById('resumoCalculos').innerHTML = '';
      document.getElementById('statusRibana').innerHTML = '';
      document.getElementById('listaPartidas').innerHTML = '';
      document.getElementById('opsGeradas').innerHTML = '';
      listaOPsGeradas = [];

      // 🔄 Recarrega dropdowns para novo uso
      google.script.run.withSuccessHandler(popularDropdowns).getDropDown();
    })
    .withFailureHandler(erro => {
      alert(`❌ Erro ao gravar a entrada: ${erro.message}`);
      console.error("⛔ Erro no salvarEntradaCompleta:", erro);
    })
    .salvarEntradaCompleta(dados);
}

</script>

</body>
</html>

// 📦 backendTecido.gs | Painel Entrada de Tecido - Versão Final

// ======================================================================
// 🔁 1. doGet: renderiza o HTML principal do painel
// ======================================================================
function doGet(e) {
  const painel = "painelTecido";
  const template = HtmlService.createTemplateFromFile(painel);
  return template.evaluate().setTitle("Entrada de Tecido").setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}


// ======================================================================
// 📥 2. getDropDown: busca opções únicas para os campos de seleção
// ======================================================================
function getDropDown() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaProdutos = ss.getSheetByName("produto_consumo_custo");
  const abaValidacao = ss.getSheetByName("validacao_suspensa");

  if (!abaProdutos || !abaValidacao)
    throw new Error("❌ Abas de suporte não encontradas.");

  return {
    produtos: [...new Set(abaProdutos.getRange("A2:A").getValues().flat().filter(Boolean))],
    malharias: [...new Set(abaProdutos.getRange("R2:R").getValues().flat().filter(Boolean))],
    cores: [...new Set(abaValidacao.getRange("E2:E").getValues().flat().filter(Boolean))],
    cortadores: [...new Set(abaValidacao.getRange("M2:M").getValues().flat().filter(Boolean))],
    confecções: [...new Set(abaValidacao.getRange("G2:G").getValues().flat().filter(Boolean))],
  };
}


// ======================================================================
// 🧵 3. getTecidosDoProduto: retorna os tecidos relacionados ao produto
// ======================================================================
function getIndice(headers, nomeExato) {
  return headers.findIndex(h => h.trim().toLowerCase().normalize("NFD").replace(/\p{Diacritic}/gu, '') ===
                                nomeExato.trim().toLowerCase().normalize("NFD").replace(/\p{Diacritic}/gu, ''));
}

function getTecidosDoProduto(produto) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("produto_consumo_custo");
  if (!aba) throw new Error("❌ Aba 'produto_consumo_custo' não encontrada.");

  const dados = aba.getDataRange().getValues();
  const headers = dados[0].map(h => String(h).trim());

  const idxProduto      = getIndice(headers, "Produto");
  const idxPrincipal    = getIndice(headers, "Tecido Principal");
  const idxComplementar = getIndice(headers, "Tecido complementar 1 e Aviamentos");
  const idxAviamento    = getIndice(headers, "Tecido_Aviamentos_2");

  if (idxProduto === -1 || idxPrincipal === -1)
    throw new Error("❌ Colunas essenciais não encontradas: 'Produto' ou 'Tecido Principal'.");

  for (let i = 1; i < dados.length; i++) {
    const nomeProduto = (dados[i][idxProduto] ?? "").toString().trim();
    if (nomeProduto.toUpperCase() === produto.trim().toUpperCase()) {
      return {
        principal: dados[i][idxPrincipal] || "",
        complementar: dados[i][idxComplementar] || "",
        aviamento: dados[i][idxAviamento] || ""
      };
    }
  }

  return { principal: '', complementar: '', aviamento: '' };
}


// ======================================================================
// 📊 4. buscarDadosProdutoCompleto: retorna consumo e valor do produto
// ======================================================================
function buscarDadosProdutoCompleto(produto, malharia) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("produto_consumo_custo");
  if (!aba) throw new Error("❌ Aba de produto não encontrada.");

  const dados = aba.getDataRange().getValues();
  const headers = dados[0].map(h => String(h).trim());

  const idxProduto   = getIndice(headers, "Produto");
  const idxConsumo   = getIndice(headers, "Consumo por PC");
  const idxValor     = getIndice(headers, "Valor KG Tecido");

  if (idxProduto === -1 || idxConsumo === -1 || idxValor === -1)
    throw new Error("❌ Colunas essenciais não encontradas: Produto, Consumo por PC ou Valor KG Tecido.");

  for (let i = 1; i < dados.length; i++) {
    const nomeProduto = (dados[i][idxProduto] ?? "").toString().trim();
    if (nomeProduto.toUpperCase() === produto.trim().toUpperCase()) {
      return {
        consumoPorPc: parseFloat(dados[i][idxConsumo]) || 0,
        valorKgPrincipal: parseFloat(dados[i][idxValor]) || 0
      };
    }
  }

  return null;
}


// ======================================================================
// 🔢 5. buscarRolosMaximosPorCorte: busca quantos rolos por corte o produto comporta
// ======================================================================
function buscarRolosMaximosPorCorte(produto) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("produto_consumo_custo");
  if (!aba) throw new Error("❌ Aba de produto não encontrada.");

  const dados = aba.getDataRange().getValues();
  const headers = dados[0].map(h => String(h).trim().toLowerCase());

  const idxProduto = headers.indexOf("produto");
  const idxRolosMax = headers.findIndex(h => h.includes("rolos") && h.includes("corte"));

  if (idxProduto === -1 || idxRolosMax === -1)
    throw new Error("❌ Coluna 'Produto' ou 'Rolos por Corte' não encontrada.");

  for (let i = 1; i < dados.length; i++) {
    const nomeProduto = String(dados[i][idxProduto] || "").trim();
    if (nomeProduto.toUpperCase() === produto.trim().toUpperCase()) {
      const valor = parseInt(dados[i][idxRolosMax]);
      return isNaN(valor) ? 0 : valor;
    }
  }

  return 0;
}


// 📦 backendTecido.gs | Painel Entrada de Tecido - Registro com Linha Mãe + Linhas por OP

function salvarEntradaCompleta(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  if (!aba) throw new Error("❌ Aba de destino não encontrada.");

  const hoje = new Date();
  const idEntrada = `ENTRADA-${Utilities.getUuid().slice(0, 8).toUpperCase()}`;
  const consumoPorPc = dados.pcsEstimadas > 0 ? dados.kgPrincipal / dados.pcsEstimadas : 0;

  // 💾 1. Grava a LINHA MÃE (consolidado geral)
  aba.appendRow([
    hoje, idEntrada, 'Mãe',
    dados.tipoEntrada, dados.produto, dados.malharia, dados.cor, dados.tecido,
    dados.romaneio, dados.dataEnvio, dados.responsavel,
    dados.kgPrincipal, dados.rolosPrincipal,
    dados.kgComplementar, dados.rolosComplementar,
    dados.kgAviamento, dados.rolosAviamento,
    dados.kgRibana, dados.rolosRibana,
    dados.pcsEstimadas, dados.totalKg, dados.totalRolos,
    dados.valorTotalSemVies, dados.kgVies, dados.rolosVies, dados.valorVies, dados.valorFinal,
    dados.dataVencimento, dados.statusRibana, dados.cortador,
    '', '', '', '', ''
  ]);


  // 📐 2. Para cada OP gerada, calcula com base nos rolos da partida
  dados.opDestinoList.forEach(linha => {
    const partida = dados.partidas.find(p => String(p.id) === String(linha.partidaId));
    if (!partida) return; // ⛔ ignora se a partida não for encontrada

    const rolosInformados = parseInt(partida.rolos || 0);
    const kgEstimado = rolosInformados * 18.5;
    const pcsEstimadas = consumoPorPc > 0 ? Math.floor(kgEstimado / consumoPorPc) : 0;

    const valorProporcional = (kgEstimado / dados.kgPrincipal) * dados.valorTotalSemVies;
    const valorFinalProporcional = valorProporcional + ((kgEstimado / dados.kgPrincipal) * dados.valorVies);

    aba.appendRow([
      hoje, idEntrada, 'Detalhe',
      dados.tipoEntrada, dados.produto, dados.malharia, dados.cor, dados.tecido,
      dados.romaneio, dados.dataEnvio, dados.responsavel,
      kgEstimado, rolosInformados,
      0, 0,
      0, 0,
      0, 0,
      pcsEstimadas, kgEstimado, rolosInformados,
      valorProporcional, '', '', '', valorFinalProporcional,
      dados.dataVencimento, dados.statusRibana, dados.cortador,
      linha.op, linha.confeccao, linha.partidaId, linha.indexCorte, linha.totalCortes
    ]);
  }); // ← aqui o fechamento correto do forEach
}


// 📐 3. Buscar Código do Fornecedor na Matriz- Coluna A 
function buscarCodigoFornecedor(nomeConfec) {
  if (!nomeConfec) return "NA1";
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("matriz_fornecimento");
  const dados = aba.getDataRange().getValues();

  const nomeNorm = normalizarTexto(nomeConfec);

  for (let i = 1; i < dados.length; i++) {
    const nomeLinha = normalizarTexto(dados[i][1]); // coluna B = nome
    const codigo = dados[i][0]; // coluna A = código
    if (nomeLinha.includes(nomeNorm)) return codigo || "NA1";
  }

  return "NA1";
}


este painel de Tecido também deve contemplar o modo de PROGRAMAÇÃO> previsto na V1 que estamos fazendo no lovable

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>✂️ Painel de Corte - Orbitta x Berzerk</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    /* Estilos gerais para a fonte Poppins */
    body { font-family: 'Poppins', sans-serif; }
    /* Estilo para caixas de resumo/informação */
    .resumo-box {
      background-color: #ebf8ff;
      border: 1px solid #bee3f8;
      border-radius: 0.5rem;
      padding: 1rem;
      margin-top: 1rem;
      font-size: 0.875rem;
      color: #2a4365;
    }
    /* Estilo para subtítulos em seções */
    .subtitulo {
      font-size: 1.125rem;
      font-weight: 600;
      margin-top: 1.5rem;
      margin-bottom: 0.5rem;
      color: #4a5568;
    }
    /* Estilo para o campo oculto */
    .hidden { display: none; }
  </style>
</head>
<body class="bg-gray-100 p-6">
  <header class="bg-blue-600 text-white p-4 rounded-t-lg shadow-md flex justify-between items-center">
    <h1 class="text-2xl font-bold">Painel de Corte</h1>
    <div class="text-right">
      <p class="text-sm">Usuário: <span id="nomeUsuario">Carregando...</span></p>
      <p class="text-sm">Data: <span id="dataAtual">Carregando...</span></p>
    </div>
  </header>

  <main class="bg-white p-6 rounded-b-lg shadow-md mb-6">
    <section class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
      <div class="bg-green-100 p-4 rounded-lg shadow-sm text-center">
        <h3 class="text-lg font-semibold text-green-800">Tecidos Recebidos no Corte</h3>
        <p class="text-2xl font-bold text-green-700" id="rolosRecebidosPainel">-</p>
      </div>
      <div class="bg-blue-100 p-4 rounded-lg shadow-sm text-center">
        <h3 class="text-lg font-semibold text-blue-800">Tecidos Enfestados & Cortados</h3>
        <p class="text-2xl font-bold text-blue-700" id="rolosEnfestadosCortadosPainel">-</p>
      </div>
      <div class="bg-yellow-100 p-4 rounded-lg shadow-sm text-center">
        <h3 class="text-lg font-semibold text-yellow-800">Tecidos Aguardando Corte</h3>
        <p class="text-2xl font-bold text-yellow-700" id="rolosAguardandoCortePainel">-</p>
      </div>
      <div class="bg-red-100 p-4 rounded-lg shadow-sm text-center">
        <h3 class="text-lg font-semibold text-red-800">Tecidos Aguardando Recebimento</h3>
        <p class="text-2xl font-bold text-red-700" id="rolosAguardandoRecebimentoPainel">-</p>
      </div>
    </section>

    <div class="mb-6">
      <label for="modoCorte" class="block text-gray-700 text-sm font-bold mb-2">Selecione o Modo:</label>
      <select id="modoCorte" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
        <option value="">-- Selecione uma opção --</option>
        <option value="recebimento">Recebimento de Tecido</option>
        <option value="enfesto_corte">Enfesto e Corte</option>
      </select>
    </div>

    <section id="blocoBBE" class="mb-6">
      <h2 class="subtitulo">Evidências de Romaneio/Partida Aguardando Recebimento (BBE)</h2>
      <div class="resumo-box">
        <ul id="listaEvidenciasBBE" class="list-disc ml-5">
          <li>Nenhuma evidência carregada...</li>
        </ul>
      </div>
    </section>
<section id="blocoRecebimentoTecido" class="hidden">
  <h2 class="subtitulo">Recebimento de Tecido</h2>

  <div class="mb-4">
    <label for="malhariaRecebimento" class="block text-gray-700 text-sm font-bold mb-2">Malharia:</label>
    <select id="malhariaRecebimento" class="form-select w-full p-2 border rounded" required>
      <option value="">🔍 Selecione...</option>
    </select>
  </div>

  <div class="mb-4">
    <label for="tecidoRecebimento" class="block text-gray-700 text-sm font-bold mb-2">Tecido:</label>
    <select id="tecidoRecebimento" class="form-select w-full p-2 border rounded" disabled required>
      <option value="">🔍 Selecione...</option>
    </select>
  </div>

  <div class="mb-4">
    <label for="romaneioRecebimento" class="block text-gray-700 text-sm font-bold mb-2">Romaneio/NF:</label>
    <select id="romaneioRecebimento" class="form-select w-full p-2 border rounded" disabled required>
      <option value="">🔍 Selecione...</option>
    </select>
  </div>

  <!-- Tabela de partidas -->
  <div id="blocoTabelaPartidas" class="hidden mt-6">
    <h3 class="font-bold text-md mb-2">Preencha os dados recebidos por partida:</h3>
    <table class="min-w-full bg-white border border-gray-200">
      <thead>
        <tr>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">ID Partida</th>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">Produto</th>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">Cor</th>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">Rolos Pendentes</th>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">Rolos Recebidos</th>
          <th class="py-2 px-4 border-b text-left text-sm font-semibold text-gray-600">KG Recebidos</th>
        </tr>
      </thead>
      <tbody id="tabelaPartidasBody"></tbody>
    </table>
  </div>

  <!-- Resumo do romaneio -->
  <div id="resumoRecebimento" class="resumo-box hidden mt-6">
    <h3 class="font-bold text-md mb-2">Resumo do Romaneio Selecionado:</h3>
    <div id="resumoRomaneioInfo"></div>
  </div>

  <!-- Botão de confirmação -->
  <div class="mt-4">
    <button id="btnConfirmarRecebimento" class="hidden bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
      Confirmar Recebimento
    </button>
  </div>
</section>


    <section id="blocoEnfesto" class="hidden">
      <h2 class="subtitulo">Enfesto e Corte</h2>

      <div class="mb-4">
        <label for="partidaEnfestada" class="block text-gray-700 text-sm font-bold mb-2">Partida Enfestada:</label>
        <select id="partidaEnfestada" class="form-select w-full p-2 border rounded" required>
          <option value="">🔍 Selecione...</option>
          </select>
      </div>

      <div id="infoPartida" class="resumo-box mb-4">
        <h3 class="font-bold text-md mb-2">Informações da Partida:</h3>
        <p><strong>Produto:</strong> <span id="infoProduto"></span></p>
        <p><strong>Cor:</strong> <span id="infoCor"></span></p>
        <p><strong>Malharia:</strong> <span id="infoMalharia"></span></p>
        <p><strong>Tecido:</strong> <span id="infoTecido"></span></p>
        <p><strong>Romaneio:</strong> <span id="infoRomaneio"></span></p>
        <p><strong>Rolos Nesta Partida:</strong> <span id="infoRolos"></span></p>
        <p><strong>Expectativa Peças (BBE):</strong> <span id="infoEstimativa"></span></p>
        <p><strong>OPs de Corte Vinculadas:</strong> <span id="infoOpsCorte"></span></p>
      </div>


      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div>
          <label for="usuarioCorte" class="block text-gray-700 text-sm font-bold mb-2">Responsável pelo Corte:</label>
          <select id="usuarioCorte" class="form-select w-full p-2 border rounded" required>
            <option value="">🔍 Selecione...</option>
            <option value="Jorge">Jorge</option>
            <option value="Kadu">Kadu</option>
            <option value="Kado">Kado</option>
            <option value="Grandão">Grandão</option>
            <option value="Dafé">Dafé</option>
          </select>
          <input type="text" id="usuarioOutro" class="form-input w-full p-2 border rounded mt-2 hidden" placeholder="Nome do Outro Responsável">
        </div>
        <div>
          <label for="inputRolosEnfestados" class="block text-gray-700 text-sm font-bold mb-2">Nº de Rolos Enfestados:</label>
          <input type="number" id="inputRolosEnfestados" class="form-input w-full p-2 border rounded" value="0" required>
        </div>
        <div>
          <label for="inputFolhas" class="block text-gray-700 text-sm font-bold mb-2">Nº de Folhas Cortadas:</label>
          <input type="number" id="inputFolhas" class="form-input w-full p-2 border rounded" value="0" required>
        </div>
        <div>
          <label for="inicioCorte" class="block text-gray-700 text-sm font-bold mb-2">Início do Corte:</label>
          <input type="datetime-local" id="inicioCorte" class="form-input w-full p-2 border rounded" required>
        </div>
        <div>
          <label for="fimCorte" class="block text-gray-700 text-sm font-bold mb-2">Fim do Corte:</label>
          <input type="datetime-local" id="fimCorte" class="form-input w-full p-2 border rounded" required>
        </div>
      </div>

      <div class="subtitulo mt-4">Grade de Corte (Por Folha):</div>
      <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
        <div>
          <label for="gradeP" class="block text-gray-700 text-sm font-bold mb-2">P:</label>
          <input type="number" id="gradeP" class="form-input w-full p-2 border rounded" value="0">
        </div>
        <div>
          <label for="gradeM" class="block text-gray-700 text-sm font-bold mb-2">M:</label>
          <input type="number" id="gradeM" class="form-input w-full p-2 border rounded" value="0">
        </div>
        <div>
          <label for="gradeG" class="block text-gray-700 text-sm font-bold mb-2">G:</label>
          <input type="number" id="gradeG" class="form-input w-full p-2 border rounded" value="0">
        </div>
        <div>
          <label for="gradeGG" class="block text-gray-700 text-sm font-bold mb-2">GG:</label>
          <input type="number" id="gradeGG" class="form-input w-full p-2 border rounded" value="0">
        </div>
        <div>
          <label for="gradeXG" class="block text-gray-700 text-sm font-bold mb-2">XG:</label>
          <input type="number" id="gradeXG" class="form-input w-full p-2 border rounded" value="0">
        </div>
      </div>

      <div id="resultadoEstimativa" class="resumo-box hidden mb-4">
        </div>
      <div class="mb-4">
        <label for="pcsEstimadasAuto" class="block text-gray-700 text-sm font-bold mb-2">Peças Estimadas (Auto):</label>
        <span id="pcsEstimadasAuto" class="form-input-display w-full p-2 border rounded bg-gray-100">0</span>
      </div>

      <div class="mb-4">
        <label for="bateuCorte" class="block text-gray-700 text-sm font-bold mb-2">O corte bateu com a grade/estimativa?</label>
        <select id="bateuCorte" class="form-select w-full p-2 border rounded" required>
          <option value="sim">Sim</option>
          <option value="nao">Não (Inserir Quantidades Manuais)</option>
        </select>
      </div>

      <div id="inputsCorteReal" class="hidden">
        <div class="subtitulo mt-4">Quantidade Cortada (Manual):</div>
        <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
          <div>
            <label for="tamP" class="block text-gray-700 text-sm font-bold mb-2">P:</label>
            <input type="number" id="tamP" class="form-input w-full p-2 border rounded" value="0">
          </div>
          <div>
            <label for="tamM" class="block text-gray-700 text-sm font-bold mb-2">M:</label>
            <input type="number" id="tamM" class="form-input w-full p-2 border rounded" value="0">
          </div>
          <div>
            <label for="tamG" class="block text-gray-700 text-sm font-bold mb-2">G:</label>
            <input type="number" id="tamG" class="form-input w-full p-2 border rounded" value="0">
          </div>
          <div>
            <label for="tamGG" class="block text-gray-700 text-sm font-bold mb-2">GG:</label>
            <input type="number" id="tamGG" class="form-input w-full p-2 border rounded" value="0">
          </div>
          <div>
            <label for="tamXG" class="block text-gray-700 text-sm font-bold mb-2">XG:</label>
            <input type="number" id="tamXG" class="form-input w-full p-2 border rounded" value="0">
          </div>
        </div>
      </div>

      <div class="subtitulo mt-4">Detalhamento do Corte:</div>
      <div class="mb-4">
        <label for="rolosBloqueados" class="block text-gray-700 text-sm font-bold mb-2">Nº de Rolos Bloqueados:</label>
        <input type="number" id="rolosBloqueados" class="form-input w-full p-2 border rounded" value="0">
      </div>
      <div class="mb-4">
        <label for="motivosCorte" class="block text-gray-700 text-sm font-bold mb-2">Motivos de Bloqueio (Se houver):</label>
        <textarea id="motivosCorte" rows="2" class="form-textarea w-full p-2 border rounded"></textarea>
      </div>
      <div class="mb-4">
        <label for="houveRetalho" class="block text-gray-700 text-sm font-bold mb-2">Houve Retalho?</label>
        <select id="houveRetalho" class="form-select w-full p-2 border rounded">
          <option value="nao">Não</option>
          <option value="sim">Sim</option>
        </select>
      </div>
      <div class="mb-4">
        <label for="numeroVolumes" class="block text-gray-700 text-sm font-bold mb-2">Nº de Volumes Gerados:</label>
        <input type="number" id="numeroVolumes" class="form-input w-full p-2 border rounded" value="0">
      </div>
      <div class="mb-4">
        <label for="obsEnfesto" class="block text-gray-700 text-sm font-bold mb-2">Observações Adicionais:</label>
        <textarea id="obsEnfesto" rows="3" class="form-textarea w-full p-2 border rounded"></textarea>
      </div>

      <button id="btnGerarResumoCorte" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
        Gerar Resumo do Corte
      </button>

      <div id="resumoCorteEnfesto" class="resumo-box hidden mt-6">
        <h3 class="font-bold text-md mb-2">Resumo Detalhado do Corte:</h3>
        <ul id="resumoCorteLista" class="list-disc ml-5">
          </ul>
      </div>

      <div id="blocoRVA" class="resumo-box hidden mt-6">
        <h3 class="font-bold text-lg mb-2 text-center text-blue-800">Resumo Visual Alinhado (RVA)</h3>
        <div id="resumoRVAContent" class="text-sm">
          </div>
        <button id="btnConfirmarAcaoFinal" class="mt-4 bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-full">
          CONFIRMAR AÇÃO FINAL
        </button>
        <div id="etiquetaCorte" class="hidden mt-4">
          <h3 class="font-bold text-md mb-2">Etiqueta de Corte Gerada:</h3>
          <div id="etiquetaCorteLista" class="border p-4 bg-white">
            </div>
        </div>
      </div>
    </section>
  </main>

  <script>

// ------------------------
// BLOCO 0 - Variáveis globais
// ------------------------
let currentCorteResumo = null;
let currentUserEmail = null;
let recebimentoListenersInit = false; // só listeners, não dados!

// ------------------------
// BLOCO 1 - Função: Alterna campo "Outro" usuário
// ------------------------
function toggleUsuarioOutro() {
  const selectUsuario = document.getElementById("usuarioCorte");
  const inputOutro = document.getElementById("usuarioOutro");
  if (selectUsuario.value === "Outro") {
    inputOutro.classList.remove("hidden");
    inputOutro.focus();
  } else {
    inputOutro.classList.add("hidden");
    inputOutro.value = "";
  }
}

// ------------------------
// BLOCO 2 - Função: Calcula estimativa de peças
// ------------------------
function calcularEstimativaGrade() {
  const gradeP = parseInt(document.getElementById('gradeP').value) || 0;
  const gradeM = parseInt(document.getElementById('gradeM').value) || 0;
  const gradeG = parseInt(document.getElementById('gradeG').value) || 0;
  const gradeGG = parseInt(document.getElementById('gradeGG').value) || 0;
  const gradeXG = parseInt(document.getElementById('gradeXG').value) || 0;
  const numFolhas = parseInt(document.getElementById('inputFolhas').value) || 0;
  const totalPecasPorFolha = gradeP + gradeM + gradeG + gradeGG + gradeXG;
  const totalPecasEstimadas = totalPecasPorFolha * numFolhas;
  const resultadoDiv = document.getElementById('resultadoEstimativa');
  if (totalPecasEstimadas > 0) {
    resultadoDiv.classList.remove('hidden');
    resultadoDiv.innerHTML = `<p><strong>Total de Peças Estimadas:</strong> ${totalPecasEstimadas}</p>
    <p><strong>Peças por Folha:</strong> ${totalPecasPorFolha}</p>`;
  } else {
    resultadoDiv.classList.add('hidden');
    resultadoDiv.innerHTML = '';
  }
  document.getElementById('pcsEstimadasAuto').innerText = totalPecasEstimadas;
}

// ------------------------
// BLOCO 3 - Função: Exibe/oculta inputs para corte manual
// ------------------------
function exibirInputsCorte() {
  const bateuCorteSelect = document.getElementById("bateuCorte");
  const inputsCorteRealDiv = document.getElementById("inputsCorteReal");
  if (bateuCorteSelect.value === "nao") {
    inputsCorteRealDiv.classList.remove("hidden");
  } else {
    inputsCorteRealDiv.classList.add("hidden");
    const gradeInputs = ['tamP', 'tamM', 'tamG', 'tamGG', 'tamXG'];
    gradeInputs.forEach(id => {
      document.getElementById(id).value = '0';
    });
  }
}

// ------------------------
// BLOCO 4 - Função: Carrega partidas para enfesto/corte
// ------------------------
function carregarPartidasEnfestadas() {
  google.script.run.withSuccessHandler(partidas => {
    const select = document.getElementById("partidaEnfestada");
    select.innerHTML = '<option value="">🔍 Selecione...</option>';
    if (partidas && partidas.length > 0) {
      partidas.forEach(p => {
        const opt = document.createElement("option");
        opt.value = p.partida;
        opt.textContent = `🧶 Partida: ${p.partida} | ${p.rolos || "?"} rolos | ${p.malharia || "-"} | ${p.cor || "-"} | ${p.tecido || "-"}`;
        Object.entries(p).forEach(([k, v]) => opt.dataset[k] = v || "");
        select.appendChild(opt);
      });
    } else {
      select.innerHTML = '<option value="">Nenhuma partida disponível para enfesto.</option>';
    }
  }).getPartidasDisponiveisParaEnfesto();
}
window.carregarPartidasEnfestadas = carregarPartidasEnfestadas;

// ------------------------
// BLOCO 5 - Função: Carrega malharias no select de recebimento
// ------------------------
function carregarMalhariasDisponiveis() {
  google.script.run.withSuccessHandler(malharias => {
    const select = document.getElementById("malhariaRecebimento");
    select.innerHTML = '<option value="">🔍 Selecione...</option>';
    malharias.forEach(m => {
      const opt = document.createElement("option");
      opt.value = m;
      opt.textContent = m;
      select.appendChild(opt);
    });
  }).getMalhariasDisponiveis();
}

// ===========================================
//BLOCO 6
// ===========================================
// Gera um resumo do corte com base nos dados inseridos e exibe-o na interface.
function gerarResumoCorte() {
  const partidaId = document.getElementById('partidaEnfestada').value;
  const responsavel = document.getElementById('usuarioCorte').value === 'Outro' ? document.getElementById('usuarioOutro').value : document.getElementById('usuarioCorte').value;
  const obsEnfesto = document.getElementById('obsEnfesto').value;
  const rolosBloqueados = document.getElementById('rolosBloqueados').value;
  const motivosCorte = document.getElementById('motivosCorte').value;
  const houveRetalho = document.getElementById('houveRetalho').value;
  const numeroVolumes = document.getElementById('numeroVolumes').value;
  const inputRolosEnfestados = document.getElementById('inputRolosEnfestados').value;
  const inputFolhas = parseInt(document.getElementById('inputFolhas').value) || 0;
  const bateuCorte = document.getElementById('bateuCorte').value;
  const inicioCorte = document.getElementById('inicioCorte').value;
  const fimCorte = document.getElementById('fimCorte').value;

  const gradeP = parseInt(document.getElementById('gradeP').value) || 0;
  const gradeM = parseInt(document.getElementById('gradeM').value) || 0;
  const gradeG = parseInt(document.getElementById('gradeG').value) || 0;
  const gradeGG = parseInt(document.getElementById('gradeGG').value) || 0;
  const gradeXG = parseInt(document.getElementById('gradeXG').value) || 0;

  let tamP = parseInt(document.getElementById('tamP').value) || 0;
  let tamM = parseInt(document.getElementById('tamM').value) || 0;
  let tamG = parseInt(document.getElementById('tamG').value) || 0;
  let tamGG = parseInt(document.getElementById('tamGG').value) || 0;
  let tamXG = parseInt(document.getElementById('tamXG').value) || 0;

  if (bateuCorte === 'sim') {
    tamP = gradeP * inputFolhas;
    tamM = gradeM * inputFolhas;
    tamG = gradeG * inputFolhas;
    tamGG = gradeGG * inputFolhas;
    tamXG = gradeXG * inputFolhas;
  }

  const totalPecasCortadas = tamP + tamM + tamG + tamGG + tamXG;
  const totalPecasEstimadas = (gradeP + gradeM + gradeG + gradeGG + gradeXG) * inputFolhas;

  currentCorteResumo = {
    partida: partidaId,
    responsavel,
    obsEnfesto,
    rolosBloqueados,
    motivosCorte,
    houveRetalho,
    numeroVolumes,
    rolosEnfestados: inputRolosEnfestados,
    numeroFolhas: inputFolhas,
    grade: { P: gradeP, M: gradeM, G: gradeG, GG: gradeGG, XG: gradeXG },
    pecasCortadasPorTamanho: { P: tamP, M: tamM, G: tamG, GG: tamGG, XG: tamXG },
    totalPecasCortadas,
    totalPecasEstimadas,
    inicioCorte,
    fimCorte,
    corteBateu: bateuCorte,
    produto: document.getElementById('infoProduto').innerText,
    cor: document.getElementById('infoCor').innerText,
    malharia: document.getElementById('infoMalharia').innerText,
    tecido: document.getElementById('infoTecido').innerText,
    romaneio: document.getElementById('infoRomaneio').innerText
  };

  const resumoLista = document.getElementById("resumoCorteLista");
  resumoLista.innerHTML = `
    <li><strong>Partida:</strong> ${currentCorteResumo.partida}</li>
    <li><strong>Responsável:</strong> ${currentCorteResumo.responsavel}</li>
    <li><strong>Início do Corte:</strong> ${currentCorteResumo.inicioCorte ? new Date(currentCorteResumo.inicioCorte).toLocaleString('pt-BR') : 'N/A'}</li>
    <li><strong>Fim do Corte:</strong> ${currentCorteResumo.fimCorte ? new Date(currentCorteResumo.fimCorte).toLocaleString('pt-BR') : 'N/A'}</li>
    <li><strong>Rolos Enfestados:</strong> ${currentCorteResumo.rolosEnfestados}</li>
    <li><strong>Nº de Folhas Cortadas:</strong> ${currentCorteResumo.numeroFolhas}</li>
    <li><strong>Grade de Corte:</strong> P:${currentCorteResumo.grade.P}, M:${currentCorteResumo.grade.M}, G:${currentCorteResumo.grade.G}, GG:${currentCorteResumo.grade.GG}, XG:${currentCorteResumo.grade.XG}</li>
    <li><strong>Quant. Cortada (Total):</strong> ${currentCorteResumo.totalPecasCortadas} peças</li>
    <li><strong>Quant. Cortada por Tamanho:</strong> P:${currentCorteResumo.pecasCortadasPorTamanho.P}, M:${currentCorteResumo.pecasCortadasPorTamanho.M}, G:${currentCorteResumo.pecasCortadasPorTamanho.G}, GG:${currentCorteResumo.pecasCortadasPorTamanho.GG}, XG:${currentCorteResumo.pecasCortadasPorTamanho.XG}</li>
    <li><strong>Rolos Bloqueados:</strong> ${currentCorteResumo.rolosBloqueados || 'Nenhum'}</li>
    <li><strong>Motivos:</strong> ${currentCorteResumo.motivosCorte || 'Nenhum'}</li>
    <li><strong>Houve Retalho:</strong> ${currentCorteResumo.houveRetalho === 'sim' ? 'Sim' : 'Não'}</li>
    <li><strong>Nº de Volumes:</strong> ${currentCorteResumo.numeroVolumes || 'N/A'}</li>
    <li><strong>Observações:</strong> ${currentCorteResumo.obsEnfesto || 'Nenhuma'}</li>
  `;
  document.getElementById("resumoCorteEnfesto").classList.remove("hidden");
  document.getElementById("blocoRVA").classList.remove("hidden");
  renderizarRVA(currentCorteResumo);
}

// Renderiza o Resumo Visual Alinhado (RVA)
function renderizarRVA(resumo) {
  const rvaContent = document.getElementById("resumoRVAContent");
  rvaContent.innerHTML = `
    <p><strong>Produto:</strong> ${resumo.produto}</p>
    <p><strong>Cor:</strong> ${resumo.cor}</p>
    <p><strong>Malharia:</strong> ${resumo.malharia}</p>
    <p><strong>Tecido:</strong> ${resumo.tecido}</p>
    <p><strong>Romaneio:</strong> ${resumo.romaneio}</p>
    <p><strong>Partida:</strong> ${resumo.partida}</p>
    <p><strong>Responsável:</strong> ${resumo.responsavel}</p>
    <p><strong>Rolos Enfestados:</strong> ${resumo.rolosEnfestados}</p>
    <p><strong>Folhas Cortadas:</strong> ${resumo.numeroFolhas}</p>
    <p><strong>Total de Peças Cortadas:</strong> ${resumo.totalPecasCortadas}</p>
    <p><strong>Início do Corte:</strong> ${resumo.inicioCorte ? new Date(resumo.inicioCorte).toLocaleString('pt-BR') : 'N/A'}</p>
    <p><strong>Fim do Corte:</strong> ${resumo.fimCorte ? new Date(resumo.fimCorte).toLocaleString('pt-BR') : 'N/A'}</p>
  `;
}

// ------------------------
// BLOCO 7 - Função: Sucesso de registro de corte
// ------------------------
function handleCorteSuccess(response) {
  alert("✅ Corte registrado com sucesso!");
  document.getElementById("blocoEnfesto").classList.add("hidden");
  document.getElementById("resumoCorteEnfesto").classList.add("hidden");
  document.getElementById("blocoRVA").classList.add("hidden");
  document.getElementById("modoCorte").value = "";
  carregarResumoPainel();
  carregarEvidenciasBBE();
  carregarPartidasEnfestadas();
  if (response && response.etiquetaHtml) {
    document.getElementById("etiquetaCorte").classList.remove("hidden");
    document.getElementById("etiquetaCorteLista").innerHTML = response.etiquetaHtml;
  }
}

// ------------------------
// BLOCO 8 - Função: Confirma ação final do corte
// ------------------------
function confirmarAcaoFinalEnviarParaBackend() {
  if (!currentCorteResumo) {
    alert("❗ Gere o resumo do corte antes de confirmar.");
    return;
  }
  google.script.run
    .withSuccessHandler(function(resposta) {
      alert("✅ Corte registrado com sucesso!");
      console.log("Resposta do backend:", resposta);
    })
    .withFailureHandler(function(erro) {
      alert("❌ Erro ao registrar corte.");
      console.error("Erro:", erro);
    })
    .registrarCorteViaEnfesto(currentCorteResumo);
}
window.confirmarAcaoFinalEnviarParaBackend = confirmarAcaoFinalEnviarParaBackend;

// ------------------------
// BLOCO 9 - Inicializa/ouvinte dos dropdowns de recebimento
// ------------------------
function inicializarRecebimentoDropdownListeners() {
  if (recebimentoListenersInit) return;
  recebimentoListenersInit = true;
  // Esses listeners só precisam ser criados UMA vez na vida da página

  const malhariaSelect = document.getElementById("malhariaRecebimento");
  const tecidoSelect = document.getElementById("tecidoRecebimento");
  const romaneioSelect = document.getElementById("romaneioRecebimento");

  malhariaSelect.addEventListener("change", () => {
    const selectedMalharia = malhariaSelect.value;
    tecidoSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
    romaneioSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
    tecidoSelect.disabled = true;
    romaneioSelect.disabled = true;
    if (!selectedMalharia) return;
    google.script.run.withSuccessHandler(tecidos => {
      if (Array.isArray(tecidos) && tecidos.length > 0) {
        tecidos.forEach(t => {
          if (t) {
            const opt = document.createElement("option");
            opt.value = t;
            opt.textContent = t;
            tecidoSelect.appendChild(opt);
          }
        });
        tecidoSelect.disabled = false;
      }
    }).getTecidosPorMalharia(selectedMalharia);
  });

  tecidoSelect.addEventListener("change", () => {
    const selectedMalharia = malhariaSelect.value;
    const selectedTecido = tecidoSelect.value;
    romaneioSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
    romaneioSelect.disabled = true;
    if (!selectedMalharia || !selectedTecido) return;
    google.script.run.withSuccessHandler(romaneios => {
      if (Array.isArray(romaneios) && romaneios.length > 0) {
        romaneios.forEach(r => {
          if (r) {
            const opt = document.createElement("option");
            opt.value = r;
            opt.textContent = r;
            romaneioSelect.appendChild(opt);
          }
        });
        romaneioSelect.disabled = false;
      }
    }).getRomaneiosPorTecido(selectedMalharia, selectedTecido);
  });
}

// Amarra evento de mudança no dropdown de malharia
const selectMalharia = document.getElementById("malhariaRecebimento");
if (selectMalharia) {
  selectMalharia.addEventListener("change", () => {
    const malhariaSelecionada = selectMalharia.value;
    const selectTecido = document.getElementById("tecidoRecebimento");
    const selectRomaneio = document.getElementById("romaneioRecebimento");

    // Novo trecho: carregar partidas após escolher romaneio
selectRomaneio.addEventListener("change", () => {
  const malharia = selectMalharia.value;
  const tecido = selectTecido.value;
  const romaneio = selectRomaneio.value;

  if (malharia && tecido && romaneio) {
    console.log("🔁 Carregando partidas para:", romaneio);

    google.script.run.withSuccessHandler(partidas => {
      const tbody = document.getElementById("tabelaPartidasBody");
      tbody.innerHTML = ""; // limpa antes

      if (Array.isArray(partidas) && partidas.length > 0) {
        partidas.forEach(partida => {
          const row = document.createElement("tr");
          row.innerHTML = `
            <td class="border px-2 py-1">${partida.id}</td>
            <td class="border px-2 py-1">${partida.produto}</td>
            <td class="border px-2 py-1">${partida.cor}</td>
            <td class="border px-2 py-1">${partida.rolosPendentes}</td>
            <td class="border px-2 py-1">
              <input data-type="rolos" data-partida-id="${partida.id}" type="number" min="0" class="border p-1 w-16" />
            </td>
            <td class="border px-2 py-1">
              <input data-type="kg" data-partida-id="${partida.id}" type="number" min="0" step="0.1" class="border p-1 w-20" />
            </td>
          `;
          tbody.appendChild(row);
        });

        document.getElementById("blocoTabelaPartidas").classList.remove("hidden");
        document.getElementById("btnConfirmarRecebimento").classList.remove("hidden");

      } else {
        alert("Nenhuma partida encontrada para esse romaneio.");
      }
    }).getPartidasPorRomaneio(malharia, tecido, romaneio);
  }
});


    // Limpa os dropdowns seguintes
    selectTecido.innerHTML = "<option value=''>Selecione um tecido</option>";
    selectRomaneio.innerHTML = "<option value=''>Selecione um romaneio</option>";

    if (malhariaSelecionada) {
      console.log("🔁 Carregando tecidos para:", malhariaSelecionada);
      google.script.run.withSuccessHandler(tecidos => {
        if (Array.isArray(tecidos) && tecidos.length > 0) {
          tecidos.forEach(tecido => {
            const option = document.createElement("option");
            option.value = tecido;
            option.textContent = tecido;
            selectTecido.appendChild(option);
          });
        } else {
          console.warn("⚠️ Nenhum tecido encontrado.");
        }
      }).getTecidosPorMalharia(malhariaSelecionada);
    }
  });
}

// Amarra evento de mudança no dropdown de tecido
const selectTecido = document.getElementById("tecidoRecebimento");
if (selectTecido) {
  selectTecido.addEventListener("change", () => {
    const malharia = document.getElementById("malhariaRecebimento").value;
    const tecidoSelecionado = selectTecido.value;
    const selectRomaneio = document.getElementById("romaneioRecebimento");

    selectRomaneio.innerHTML = "<option value=''>Selecione um romaneio</option>";

    if (malharia && tecidoSelecionado) {
      console.log("🔁 Carregando romaneios para:", malharia, tecidoSelecionado);
      google.script.run.withSuccessHandler(romaneios => {
        if (Array.isArray(romaneios) && romaneios.length > 0) {
          romaneios.forEach(r => {
            const option = document.createElement("option");
            option.value = r;
            option.textContent = r;
            selectRomaneio.appendChild(option);
          });
        } else {
          console.warn("⚠️ Nenhum romaneio encontrado.");
        }
      }).getRomaneiosPorTecido(malharia, tecidoSelecionado);
    }
  });
}


// SEMPRE chame esta ao entrar no modo recebimento
function carregarMalhariasRecebimento() {
  console.log("Chamou carregarMalhariasRecebimento");

  const malhariaSelect = document.getElementById("malhariaRecebimento");
  const tecidoSelect = document.getElementById("tecidoRecebimento");
  const romaneioSelect = document.getElementById("romaneioRecebimento");

  // Reset dropdowns
  malhariaSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
  tecidoSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
  romaneioSelect.innerHTML = '<option value="">🔍 Selecione...</option>';
  tecidoSelect.disabled = true;
  romaneioSelect.disabled = true;

  google.script.run.withSuccessHandler(malharias => {
    console.log("Malharias recebidas do backend:", malharias); // <--- ADICIONE ESTA LINHA!

    if (Array.isArray(malharias) && malharias.length > 0) {
      malharias.forEach(m => {
        if (m) {
          const opt = document.createElement("option");
          opt.value = m;
          opt.textContent = m;
          malhariaSelect.appendChild(opt);
        }
      });
    } else {
      // Se vier vazio, pode mostrar uma mensagem ou logar
      console.warn("Nenhuma malharia disponível no momento.");
    }
    tecidoSelect.disabled = true;
    romaneioSelect.disabled = true;
  }).getMalhariasDisponiveis();
}

// ------------------------
// BLOCO 10 - Atualiza painel
// ------------------------
function atualizarResumoPainel(dados) {
  if (!dados) return;
  document.getElementById("rolosRecebidosPainel").innerText = dados.rolosRecebidosCorte || 0;
  document.getElementById("rolosEnfestadosPainel").innerText = dados.rolosEnfestadosCortados || 0;
  document.getElementById("rolosAguardandoCortePainel").innerText = dados.rolosAguardandoCorte || 0;
  document.getElementById("rolosAguardandoRecebimentoPainel").innerText = dados.rolosAguardandoRecebimento || 0;
}

// ------------------------
// BLOCO 11 - Evidências BBE
// ------------------------
function carregarEvidenciasBBE() {
  google.script.run.withSuccessHandler(evidencias => {
    const listaEvidencias = document.getElementById('listaEvidenciasBBE');
    listaEvidencias.innerHTML = '';
    if (evidencias.length > 0) {
      evidencias.forEach(ev => {
        const li = document.createElement('li');
        li.textContent = ev;
        listaEvidencias.appendChild(li);
      });
    } else {
      listaEvidencias.innerHTML = '<li>Nenhuma evidência de romaneio/partida aguardando recebimento no corte.</li>';
    }
  }).getMalhariasAguardandoRecebimento();
}

// ------------------------
// BLOCO 12 - Resumo painel e email usuário
// ------------------------
function carregarResumoPainel() {
  google.script.run.withSuccessHandler(resumo => {
    google.script.run.withSuccessHandler(email => {
      currentUserEmail = email;
      document.getElementById('nomeUsuario').innerText = email.split('@')[0];
      document.getElementById('dataAtual').innerText = new Date().toLocaleDateString('pt-BR', { day: '2-digit', month: '2-digit', year: 'numeric' });
    }).getUserEmail();

    document.getElementById('rolosRecebidosPainel').innerText = resumo.rolosRecebidosCorte;
    document.getElementById('rolosEnfestadosCortadosPainel').innerText = resumo.rolosEnfestadosCortados;
    document.getElementById('rolosAguardandoCortePainel').innerText = resumo.rolosAguardandoCorte;
    document.getElementById('rolosAguardandoRecebimentoPainel').innerText = resumo.rolosAguardandoRecebimento;
  }).getResumoPainel();
}

// ===========================================
// BLOCO 13 - UNIFICADO E AJUSTADO
// ===========================================

function headersMap(headerRow) {
  const map = {};
  headerRow.forEach((col, idx) => {
    const normalized = col.toString().trim().toUpperCase();
    map[normalized] = idx;
  });
  return map;
}

document.addEventListener('DOMContentLoaded', () => {
  carregarResumoPainel();
  carregarEvidenciasBBE();
  carregarPartidasEnfestadas();

  carregarMalhariasDisponiveis();
  setTimeout(() => inicializarRecebimentoDropdownListeners(), 200);

  const modoCorteSelect = document.getElementById('modoCorte');
  const blocoRecebimento = document.getElementById('blocoRecebimentoTecido');
  const blocoEnfesto = document.getElementById('blocoEnfesto');

  if (modoCorteSelect) {
    modoCorteSelect.addEventListener('change', (event) => {
      const modo = event.target.value;
      if (modo === 'recebimento') {
        blocoRecebimento.classList.remove('hidden');
        blocoEnfesto.classList.add('hidden');
        carregarEvidenciasBBE();
        carregarMalhariasDisponiveis();
        setTimeout(() => inicializarRecebimentoDropdownListeners(), 200);
      } else if (modo === 'enfesto_corte') {
        blocoRecebimento.classList.add('hidden');
        blocoEnfesto.classList.remove('hidden');
      } else {
        blocoRecebimento.classList.add('hidden');
        blocoEnfesto.classList.add('hidden');
      }
    });
  }

  const selectMalharia = document.getElementById("malhariaRecebimento");
  const selectTecido = document.getElementById("tecidoRecebimento");
  const selectRomaneio = document.getElementById("romaneioRecebimento");

  if (selectMalharia) {
    selectMalharia.addEventListener("change", () => {
      const malhariaSelecionada = selectMalharia.value;
      selectTecido.innerHTML = "<option value=''>Selecione um tecido</option>";
      selectRomaneio.innerHTML = "<option value=''>Selecione um romaneio</option>";

      if (malhariaSelecionada) {
        console.log("🔁 Carregando tecidos para:", malhariaSelecionada);
        google.script.run.withSuccessHandler(tecidos => {
          if (Array.isArray(tecidos) && tecidos.length > 0) {
            tecidos.forEach(tecido => {
              const option = document.createElement("option");
              option.value = tecido;
              option.textContent = tecido;
              selectTecido.appendChild(option);
            });
          } else {
            console.warn("⚠️ Nenhum tecido encontrado.");
          }
        }).getTecidosPorMalharia(malhariaSelecionada);
      }
    });
  }

  if (selectTecido) {
    selectTecido.addEventListener("change", () => {
      const malharia = selectMalharia.value;
      const tecidoSelecionado = selectTecido.value;
      selectRomaneio.innerHTML = "<option value=''>Selecione um romaneio</option>";

      if (malharia && tecidoSelecionado) {
        console.log("🔁 Carregando romaneios para:", malharia, tecidoSelecionado);
        google.script.run.withSuccessHandler(romaneios => {
          if (Array.isArray(romaneios) && romaneios.length > 0) {
            romaneios.forEach(r => {
              const option = document.createElement("option");
              option.value = r;
              option.textContent = r;
              selectRomaneio.appendChild(option);
            });
          } else {
            console.warn("⚠️ Nenhum romaneio encontrado.");
          }
        }).getRomaneiosPorTecido(malharia, tecidoSelecionado);
      }
    });
  }

  selectRomaneio.addEventListener("change", () => {
    const malharia = selectMalharia.value;
    const tecido = selectTecido.value;
    const romaneio = selectRomaneio.value;

    if (malharia && tecido && romaneio) {
      console.log("🔁 Carregando partidas para:", romaneio);

      google.script.run.withSuccessHandler(partidas => {
        const tbody = document.getElementById("tabelaPartidasBody");
        tbody.innerHTML = "";

        if (Array.isArray(partidas) && partidas.length > 0) {
          partidas.forEach(partida => {
            const row = document.createElement("tr");
            row.innerHTML = `
              <td class="border px-2 py-1">${partida.id}</td>
              <td class="border px-2 py-1">${partida.produto}</td>
              <td class="border px-2 py-1">${partida.cor}</td>
              <td class="border px-2 py-1">${partida.rolosPendentes}</td>
              <td class="border px-2 py-1">
                <input data-type="rolos" data-partida-id="${partida.id}" type="number" min="0" class="border p-1 w-16" />
              </td>
              <td class="border px-2 py-1">
                <input data-type="kg" data-partida-id="${partida.id}" type="number" min="0" step="0.1" class="border p-1 w-20" />
              </td>
            `;
            tbody.appendChild(row);
          });

          document.getElementById("blocoTabelaPartidas").classList.remove("hidden");
          document.getElementById("btnConfirmarRecebimento").classList.remove("hidden");

        } else {
          alert("Nenhuma partida encontrada para esse romaneio.");
        }
      }).getPartidasPorRomaneio(malharia, tecido, romaneio);
    }
  });

  document.getElementById("usuarioCorte").addEventListener("change", toggleUsuarioOutro);
  document.getElementById("inputFolhas").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeP").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeM").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeGG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeXG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("bateuCorte").addEventListener("change", exibirInputsCorte);

  const partidaEnfestadaSelect = document.getElementById("partidaEnfestada");
  if (partidaEnfestadaSelect) {
    partidaEnfestadaSelect.addEventListener("change", () => {
      const selectedPartidaId = partidaEnfestadaSelect.value;
      if (selectedPartidaId) {
        google.script.run.withSuccessHandler(dadosPartida => {
          document.getElementById('infoProduto').innerText = dadosPartida?.produto || 'N/A';
          document.getElementById('infoCor').innerText = dadosPartida?.cor || 'N/A';
          document.getElementById('infoMalharia').innerText = dadosPartida?.malharia || 'N/A';
          document.getElementById('infoTecido').innerText = dadosPartida?.tecido || 'N/A';
          document.getElementById('infoRomaneio').innerText = dadosPartida?.romaneio || 'N/A';
          document.getElementById('infoRolos').innerText = dadosPartida?.rolos || 'N/A';
          document.getElementById('infoEstimativa').innerText = dadosPartida?.expectativaPCs || 'N/A';
          document.getElementById('infoOpsCorte').innerText = dadosPartida?.opsCorte || 'N/A';
        }).getDadosEnfesto(selectedPartidaId);
      } else {
        ['infoProduto', 'infoCor', 'infoMalharia', 'infoTecido', 'infoRomaneio', 'infoRolos', 'infoEstimativa', 'infoOpsCorte'].forEach(id => {
          document.getElementById(id).innerText = '';
        });
      }
    });
  }

  document.getElementById("btnGerarResumoCorte").addEventListener("click", gerarResumoCorte);
  document.getElementById("btnConfirmarAcaoFinal").addEventListener("click", confirmarAcaoFinalEnviarParaBackend);

  document.getElementById("btnConfirmarRecebimento").addEventListener("click", () => {
    const romaneio = document.getElementById("romaneioRecebimento").value;
    if (!romaneio) {
      alert("Por favor, selecione um Romaneio antes de confirmar.");
      return;
    }
    const partidasParaRegistrar = [];
    const inputsRolos = document.querySelectorAll('#tabelaPartidasBody input[data-type="rolos"]');
    inputsRolos.forEach(input => {
      const partidaId = input.dataset.partidaId;
      const rolosRecebidos = parseInt(input.value) || 0;
      const kgInput = document.querySelector(`#tabelaPartidasBody input[data-partida-id="${partidaId}"][data-type="kg"]`);
      const kgRecebidos = parseFloat(kgInput.value) || 0;
      if (rolosRecebidos > 0 || kgRecebidos > 0) {
        partidasParaRegistrar.push({
          idPartida: partidaId,
          rolosRecebidos,
          kgRecebidos
        });
      }
    });

    if (partidasParaRegistrar.length === 0) {
      alert("Por favor, insira a quantidade de rolos ou KG para pelo menos uma partida.");
      return;
    }

    if (confirm(`Confirmar recebimento para o romaneio ${romaneio}?`)) {
      const payload = {
        romaneio,
        usuario: currentUserEmail,
        partidas: partidasParaRegistrar
      };
      google.script.run.withSuccessHandler((response) => {
        alert(response.message);
        location.reload();
      }).registrarRecebimentoPartidas(payload);
    }
  });
});


// ===========================================
//BLOCO 14
// ===========================================
  // outros eventListeners normais
  document.getElementById("usuarioCorte").addEventListener("change", toggleUsuarioOutro);
  document.getElementById("inputFolhas").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeP").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeM").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeGG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("gradeXG").addEventListener("input", calcularEstimativaGrade);
  document.getElementById("bateuCorte").addEventListener("change", exibirInputsCorte);

  // partida enfestada
  const partidaEnfestadaSelect = document.getElementById("partidaEnfestada");
  if (partidaEnfestadaSelect) {
    partidaEnfestadaSelect.addEventListener("change", () => {
      const selectedPartidaId = partidaEnfestadaSelect.value;
      if (selectedPartidaId) {
        google.script.run.withSuccessHandler(dadosPartida => {
          if (dadosPartida) {
            document.getElementById('infoProduto').innerText = dadosPartida.produto;
            document.getElementById('infoCor').innerText = dadosPartida.cor;
            document.getElementById('infoMalharia').innerText = dadosPartida.malharia;
            document.getElementById('infoTecido').innerText = dadosPartida.tecido;
            document.getElementById('infoRomaneio').innerText = dadosPartida.romaneio;
            document.getElementById('infoRolos').innerText = dadosPartida.rolos;
            document.getElementById('infoEstimativa').innerText = dadosPartida.expectativaPCs;
            document.getElementById('infoOpsCorte').innerText = dadosPartida.opsCorte;
          } else {
            document.getElementById('infoProduto').innerText = 'N/A';
            document.getElementById('infoCor').innerText = 'N/A';
            document.getElementById('infoMalharia').innerText = 'N/A';
            document.getElementById('infoTecido').innerText = 'N/A';
            document.getElementById('infoRomaneio').innerText = 'N/A';
            document.getElementById('infoRolos').innerText = 'N/A';
            document.getElementById('infoEstimativa').innerText = 'N/A';
            document.getElementById('infoOpsCorte').innerText = 'N/A';
          }
        }).getDadosEnfesto(selectedPartidaId);
      } else {
        document.getElementById('infoProduto').innerText = '';
        document.getElementById('infoCor').innerText = '';
        document.getElementById('infoMalharia').innerText = '';
        document.getElementById('infoTecido').innerText = '';
        document.getElementById('infoRomaneio').innerText = '';
        document.getElementById('infoRolos').innerText = '';
        document.getElementById('infoEstimativa').innerText = '';
        document.getElementById('infoOpsCorte').innerText = '';
      }
    });
  }

  document.getElementById("btnGerarResumoCorte").addEventListener("click", gerarResumoCorte);
  document.getElementById("btnConfirmarAcaoFinal").addEventListener("click", confirmarAcaoFinalEnviarParaBackend);

  // recebimento
  document.getElementById("btnConfirmarRecebimento").addEventListener("click", () => {
    const romaneio = document.getElementById("romaneioRecebimento").value;
    if (!romaneio) {
      alert("Por favor, selecione um Romaneio antes de confirmar.");
      return;
    }
    const partidasParaRegistrar = [];
    const inputsRolos = document.querySelectorAll('#tabelaPartidasBody input[data-type="rolos"]');
    inputsRolos.forEach(input => {
      const partidaId = input.dataset.partidaId;
      const rolosRecebidos = parseInt(input.value) || 0;
      const kgInput = document.querySelector(`#tabelaPartidasBody input[data-partida-id="${partidaId}"][data-type="kg"]`);
      const kgRecebidos = parseFloat(kgInput.value) || 0;
      if (rolosRecebidos > 0 || kgRecebidos > 0) {
        partidasParaRegistrar.push({
          idPartida: partidaId,
          rolosRecebidos: rolosRecebidos,
          kgRecebidos: kgRecebidos
        });
      }
    });

    if (partidasParaRegistrar.length === 0) {
      alert("Por favor, insira a quantidade de rolos ou KG para pelo menos uma partida.");
      return;
    }

    if (confirm(`Confirmar recebimento para o romaneio ${romaneio}?`)) {
      const payload = {
        romaneio: romaneio,
        usuario: currentUserEmail,
        partidas: partidasParaRegistrar
      };
      google.script.run.withSuccessHandler((response) => {
        alert(response.message);
        location.reload();
        carregarResumoPainel();
        carregarEvidenciasBBE();
      }).registrarRecebimentoPartidas(payload);
    }
  });

</script>
</body>
</html>

// ✅ backendCorte.gs | Refatorado com foco em recebimento baseado na linha MÃE, detalhamento nas DETALHEs e integração com log_corte

// =====================================================================
// 🔁 doGet - Renderiza o painel de corte ou enfesto conforme o parâmetro
// Esta função é o ponto de entrada da aplicação web.
// =====================================================================
function doGet(e) {
  const painel = (e && e.parameter && e.parameter.painel) ? e.parameter.painel : "painelCorte";
  const template = HtmlService.createTemplateFromFile(painel);

  // 🔽 Aqui você injeta os dados no template, para o frontend acessar via <?= ... ?>
  if (painel === "painelCorte") {
    template.resumoRomaneiosPendentes = getResumoRomaneiosPendentes(); // adiciona isso
    template.resumoCorte = getResumoPainel(); // se quiser reaproveitar dados
  }

  return template.evaluate()
    .setTitle("Painel de Corte Berzerk x Orbitta")
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}




// =====================================================================
// 🧵 getMalhariasAguardandoRecebimento - Retorna um resumo de malharias
// que possuem romaneios ou partidas aguardando recebimento no corte.
// Utilizado para o bloco de "Evidências BBE" no frontend.
// =====================================================================
function getMalhariasAguardandoRecebimento() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido"); // Planilha onde os dados de entrada são registrados
  const dados = aba.getDataRange().getValues(); // Obtém todos os dados da planilha
  const h = headersMap(dados[0]); // Mapeia os cabeçalhos para seus índices

  const mapa = {}; // Objeto para armazenar o resumo por malharia

  // Itera sobre as linhas de dados, começando da segunda linha (índice 1) para ignorar os cabeçalhos
  for (let i = 1; i < dados.length; i++) {
    const tipoLinha = (dados[i][h["TIPO LINHA"]] || "").toString().toUpperCase();
    const statusRecebimento = (dados[i][h["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();

    // Filtra apenas linhas do tipo "DETALHE" que ainda não foram "RECEBIDO"
    // A premissa fala em 'romaneios', mas o frontend aguarda 'rolos', então foca no detalhe da partida.
    if (tipoLinha === "DETALHE" && !statusRecebimento.includes("RECEBIDO NO CORTE")) {
      const malharia = (dados[i][h["MALHARIA"]] || "N/D").toString().trim();
      // O romaneio é necessário para o contexto, mas a contagem é de rolos
      const rolos = parseInt(dados[i][h["ROLOS PRINCIPAL"]]) || 0;
      const romaneio = (dados[i][h["ROMANEIO"]] || "N/D").toString().trim();

      if (!mapa[malharia]) {
        mapa[malharia] = { romaneios: new Set(), rolos: 0 }; // Usa Set para contar romaneios únicos
      }
      mapa[malharia].romaneios.add(romaneio); // Adiciona o romaneio ao Set
      mapa[malharia].rolos += rolos;
    }
  }

  // Formata o resumo para exibição no frontend
  const resumo = Object.entries(mapa).map(([malharia, dados]) =>
    `Malharia ${malharia} tem ${dados.rolos} rolos em ${dados.romaneios.size} romaneio(s) aguardando recebimento.`
  );
  return resumo;
}

// =====================================================================
// 🆕 getMalhariasDisponiveis - Retorna uma lista de malharias únicas
// com romaneios/partidas ainda não recebidos (linhas MÃE).
// Usado no select de Malharia no modo "Recebimento de Tecido".
// =====================================================================
function getMalhariasDisponiveis() {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("entrada_destinacao_tecido");
  if (!aba) throw new Error("❌ Aba 'entrada_destinacao_tecido' não encontrada.");

  const dados = aba.getDataRange().getValues();
  const header = dados[0];
  const idxMalharia = header.indexOf("Malharia");

  if (idxMalharia === -1) throw new Error("❌ Coluna 'Malharia' não encontrada no cabeçalho.");

  const malharias = [...new Set(dados.slice(1)
    .map(l => l[idxMalharia])
    .map(v => v?.toString().trim())
    .filter(Boolean))];

  Logger.log("✅ Malharias encontradas:");
  Logger.log(malharias);

  return malharias;
}


// ===========================================
// ✅ REFATORAÇÃO SUGERIDA COM BASE NO SEU CENÁRIO
// ===========================================

function headersMap(headerRow) {
  const map = {};
  headerRow.forEach((col, idx) => {
    const normalized = col
      .toString()
      .normalize("NFD") // Remove acentos
      .replace(/\p{Diacritic}/gu, "")
      .replace(/\s+/g, " ") // normaliza múltiplos espaços
      .trim()
      .toUpperCase();
    map[normalized] = idx;
  });
  return map;
}

// ===========================================
// 🔄 getTecidosPorMalharia com headersMap
// ===========================================
function getTecidosPorMalharia(malharia) {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  if (!dados || dados.length < 2) return [];

  const hEntrada = headersMap(dados[0]);
  const tecidosSet = new Set();

  dados.slice(1).forEach((linha, i) => {
    const tipoLinha = (linha[hEntrada["TIPO LINHA"]] || "").toString().trim().toUpperCase();
    const malhariaLinha = (linha[hEntrada["MALHARIA"]] || "").toString().trim().toUpperCase();
    const statusRecebimento = (linha[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().trim().toUpperCase();
    const tecido = (linha[hEntrada["TECIDO"]] || "").toString().trim();

    Logger.log(`🔎 [${i + 2}] tipo=${tipoLinha}, malharia=${malhariaLinha}, status=${statusRecebimento}, tecido=${tecido}`);

    if (
      tipoLinha === "MÃE" &&
      malhariaLinha === malharia.toUpperCase() &&
      !statusRecebimento.includes("RECEBIDO")
    ) {
      tecidosSet.add(tecido);
    }
  });

  const tecidosArray = Array.from(tecidosSet);
  Logger.log("✅ Tecidos encontrados:", tecidosArray);
  return tecidosArray;
}

// ===========================================
// 🔄 getRomaneiosPorTecido com headersMap
// ===========================================
function getRomaneiosPorTecido(malharia, tecido) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName("entrada_destinacao_tecido");
  const data = sheet.getDataRange().getValues();
  const hEntrada = headersMap(data[0]);

  const romaneiosUnicos = {};

  for (let i = 1; i < data.length; i++) {
    const row = data[i];
    const currentMalharia = (row[hEntrada["MALHARIA"]] || "").toString().toUpperCase();
    const currentTecido = (row[hEntrada["TECIDO"]] || "").toString().toUpperCase();
    const currentRomaneio = row[hEntrada["ROMANEIO"]];
    const dataRecebimento = row[hEntrada["DATA REGISTRO"]];
    const tipoLinha = (row[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();
    const statusRecebimento = (row[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();

    if (currentMalharia === malharia.toUpperCase() &&
        currentTecido === tecido.toUpperCase() &&
        currentRomaneio &&
        tipoLinha === "MÃE" &&
        !statusRecebimento.includes("RECEBIDO NO CORTE")) {

      let dataFormatada = 'N/A';
      if (dataRecebimento instanceof Date) {
        dataFormatada = Utilities.formatDate(dataRecebimento, SpreadsheetApp.getActiveSpreadsheet().getSpreadsheetTimeZone(), 'dd/MM/yy');
      } else if (typeof dataRecebimento === 'string' && dataRecebimento.trim() !== '') {
        dataFormatada = dataRecebimento;
      }

      if (!romaneiosUnicos[currentRomaneio]) {
        romaneiosUnicos[currentRomaneio] = dataFormatada;
      }
    }
  }

  const resultado = [];
  for (const romaneio in romaneiosUnicos) {
    resultado.push(`${romaneio} - ${romaneiosUnicos[romaneio]}`);
  }
  return resultado.sort();
}

// ===========================================
// 🧾 getResumoRomaneio com headersMap
// ===========================================
function getResumoRomaneio(romaneioAlvoComData, userEmail) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName("entrada_destinacao_tecido");
  const data = sheet.getDataRange().getValues();
  const hEntrada = headersMap(data[0]);

  const romaneioAlvo = romaneioAlvoComData.split(' - ')[0].trim();
  let resumo = {
    produto: "N/A",
    malharia: "N/A",
    tecido: "N/A",
    romaneio: romaneioAlvoComData,
    dataEnvio: "N/A",
    recebidoEm: "Aguardando Recebimento",
    usuario: userEmail || "N/A",
    totalRolos: 0,
    detalhesPorCor: {},
    partidasDetalhes: []
  };

  const partidasProcessadasParaDetalhes = new Set();
  const partidasProcessadasParaTotalCor = new Set();
  let foundMotherRow = false;

  for (let i = 1; i < data.length; i++) {
    const row = data[i];
    const currentRomaneioNaLinha = (row[hEntrada["ROMANEIO"]] || "").toString().trim();

    if (currentRomaneioNaLinha === romaneioAlvo) {
      const tipoLinha = (row[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();

      if (tipoLinha === "MÃE" && !foundMotherRow) {
        resumo.produto = (row[hEntrada["PRODUTO"]] || "N/A").toString().trim();
        resumo.malharia = (row[hEntrada["MALHARIA"]] || "N/A").toString().trim();
        resumo.tecido = (row[hEntrada["TECIDO"]] || "N/A").toString().trim();
        resumo.totalRolos = parseInt(row[hEntrada["ROLOS PRINCIPAL"]] || 0) || 0;

        const rawDataEnvio = row[hEntrada["DATA ENVIO"]];
        if (rawDataEnvio instanceof Date) {
          resumo.dataEnvio = Utilities.formatDate(rawDataEnvio, ss.getSpreadsheetTimeZone(), 'dd/MM/yy');
        } else if (typeof rawDataEnvio === 'string' && rawDataEnvio.trim() !== '') {
          resumo.dataEnvio = rawDataEnvio.trim();
        }

        const rawStatusRecebimento = (row[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();
        const rawDataRegistro = row[hEntrada["DATA REGISTRO"]];
        const rawResponsavel = row[hEntrada["RESPONSÁVEL"]];

        if (rawStatusRecebimento.includes("RECEBIDO NO CORTE")) {
          if (rawDataRegistro instanceof Date) {
            resumo.recebidoEm = Utilities.formatDate(rawDataRegistro, ss.getSpreadsheetTimeZone(), 'dd/MM/yy HH:mm');
          } else if (typeof rawDataRegistro === 'string' && rawDataRegistro.trim() !== '') {
            resumo.recebidoEm = rawDataRegistro.trim();
          } else {
            resumo.recebidoEm = "N/A";
          }
          resumo.usuario = (rawResponsavel || userEmail || "N/A").toString().trim();
        } else {
          resumo.recebidoEm = "Aguardando Recebimento";
          resumo.usuario = userEmail || "N/A";
        }
        foundMotherRow = true;
      }

      if (tipoLinha === "DETALHE") {
        const cor = (row[hEntrada["COR"]] || "N/A").toString().trim();
        const rolosPrincipal = parseFloat(row[hEntrada["ROLOS PRINCIPAL"]]) || 0;
        const numPartida = (row[hEntrada["ID PARTIDA"]] || "").toString().split('.')[0].trim();
        const statusCorte = (row[hEntrada["STATUS CORTE"]] || "").toString().trim();
        const statusRecebimentoDetalhe = (row[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().trim();
        const statusParaExibir = (statusCorte && statusCorte !== "N/A") ? statusCorte : statusRecebimentoDetalhe;

        const opsVinculadasString = (row[hEntrada["OP"]] || "").toString().trim();
        const corteNum = (row[hEntrada["CORTE"]] || "").toString().trim();

        if (numPartida !== "" && !partidasProcessadasParaTotalCor.has(numPartida)) {
          if (!resumo.detalhesPorCor[cor]) {
            resumo.detalhesPorCor[cor] = { rolos: 0, partidas: [] };
          }
          if (!resumo.detalhesPorCor[cor].partidas.includes(numPartida)) {
            resumo.detalhesPorCor[cor].partidas.push(numPartida);
          }
        }

        if (numPartida !== "" && !partidasProcessadasParaDetalhes.has(numPartida)) {
          let corteOpInfo = [];
          if (opsVinculadasString && opsVinculadasString !== "N/A") {
            const opsArray = opsVinculadasString.split(',').map(op => op.trim()).filter(op => op !== "");
            if (opsArray.length > 0) {
              corteOpInfo.push(`OP: ${opsArray.join(', ')}`);
            }
          }
          if (corteNum && corteNum !== "N/A") {
            corteOpInfo.push(`Corte #: ${corteNum}`);
          }
          let corteOpString = corteOpInfo.length > 0 ? corteOpInfo.join(" / ") : "N/A";

          resumo.partidasDetalhes.push(
            `Partida ${numPartida} (${rolosPrincipal} rolos) - Status: ${statusParaExibir} - ${corteOpString}`
          );
          partidasProcessadasParaDetalhes.add(numPartida);
        }
      }
    }
  }

  let htmlPorCor = '';
  for (const cor in resumo.detalhesPorCor) {
    const rolosCor = resumo.detalhesPorCor[cor].rolos;
    const numPartidasCor = resumo.detalhesPorCor[cor].partidas.length;
    htmlPorCor += `<p><strong>${cor}: ${rolosCor} rolos - ${numPartidasCor} partida(s)</strong></p>`;
  }
  resumo.htmlPorCor = htmlPorCor;
  resumo.htmlPartidasDetalhes = resumo.partidasDetalhes.map(detail => `<p>${detail}</p>`).join('');

  return resumo;
}

// =====================================================================
// 📤 registrarRecebimentoPartidas - Confirma o recebimento de partidas no frontend.
// Atualiza o STATUS CORTE na aba "entrada_destinacao_tecido" para "Tecido Recebido"
// e preenche a coluna "Data Registro" (ou outra apropriada) com a data/hora do recebimento.
// Também registra no "log_corte".
// =====================================================================
function registrarRecebimentoPartidas(payload) {
  Logger.log("--- INÍCIO: registrarRecebimentoPartidas ---");
  Logger.log("Payload recebido: %s", JSON.stringify(payload));

  const { romaneio, usuario, partidas } = payload; // romaneio completo, e.g., "66909 - 04/06/25"
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaEntradaDestinacao = ss.getSheetByName("entrada_destinacao_tecido");
  const abaLogCorte = ss.getSheetByName("log_corte"); // Certifique-se de que esta aba existe

  const dadosEntrada = abaEntradaDestinacao.getDataRange().getValues();
  const headersEntrada = dadosEntrada[0];
  const hEntrada = headersMap(headersEntrada);

  const dadosLogCorte = abaLogCorte.getDataRange().getValues();
  const headersLogCorte = dadosLogCorte[0];
  const hLogCorte = headersMap(headersLogCorte);

  Logger.log("Cabeçalhos de entrada mapeados: %s", JSON.stringify(hEntrada));
  Logger.log("Cabeçalhos de log_corte mapeados: %s", JSON.stringify(hLogCorte));


  const romaneioCurto = romaneio.split(' - ')[0].trim(); // Pega apenas o número do romaneio

  const now = new Date();
  const dataRegistro = Utilities.formatDate(now, ss.getSpreadsheetTimeZone(), 'dd/MM/yyyy HH:mm:ss');

  let motherRowIndex = -1;
  const detailedRowIndices = [];

  // 1. Encontrar a linha MÃE e as linhas DETALHE do romaneio
  for (let i = 1; i < dadosEntrada.length; i++) {
    const linha = dadosEntrada[i];
    const currentRomaneio = (linha[hEntrada["ROMANEIO"]] || "").toString().trim();
    const tipoLinha = (linha[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();

    // Use includes para pegar o romaneio pelo numero, pois o Romaneio na planilha pode ter mais info.
    if (currentRomaneio.includes(romaneioCurto)) {
      if (tipoLinha === "MÃE") {
        motherRowIndex = i;
      } else if (tipoLinha === "DETALHE") {
        // Verifica se a partida do detalhe está no payload para atualização
        const idPartidaDetalhe = (linha[hEntrada["ID PARTIDA"]] || "").toString().trim();
        const foundInPayload = partidas.some(p => p.idPartida === idPartidaDetalhe);
        if (foundInPayload) {
          detailedRowIndices.push(i);
        }
      }
    }
  }

  if (motherRowIndex === -1 && detailedRowIndices.length === 0) {
    Logger.log("ERRO: Romaneio ou partidas não encontradas na planilha de entrada_destinacao_tecido.");
    throw new Error("Romaneio ou partidas não encontradas para registro de recebimento.");
  }

  // 2. Atualizar a linha MÃE
  if (motherRowIndex !== -1) {
    const motherRow = dadosEntrada[motherRowIndex];
    const rangeToUpdate = abaEntradaDestinacao.getRange(motherRowIndex + 1, 1, 1, headersEntrada.length); // +1 para índice da linha

    // Atualiza os valores na array, antes de escrever
    motherRow[hEntrada["STATUS RECEBIMENTO TECIDO"]] = "Recebido no corte";
    motherRow[hEntrada["DATA REGISTRO"]] = dataRegistro; // Data e Hora do recebimento
    motherRow[hEntrada["RESPONSÁVEL"]] = usuario;

    // Persistir as alterações na linha MÃE
    rangeToUpdate.setValues([motherRow]);
    Logger.log("Linha MÃE (%s) atualizada para 'Recebido no corte' por '%s' em '%s'", romaneioCurto, usuario, dataRegistro);
  } else {
     Logger.log("Atenção: Linha MÃE para o romaneio %s não encontrada. Apenas linhas DETALHE serão atualizadas.", romaneioCurto);
  }

  // 3. Atualizar as linhas DETALHE e registrar no log_corte
  for (const partidaPayload of partidas) {
    const { idPartida, rolosRecebidos, kgRecebidos } = partidaPayload;
    let foundDetailedRow = false;

    for (const rowIndex of detailedRowIndices) {
      const detailedRow = dadosEntrada[rowIndex];
      const currentIdPartida = (detailedRow[hEntrada["ID PARTIDA"]] || "").toString().trim();

      if (currentIdPartida === idPartida) {
        const rangeToUpdate = abaEntradaDestinacao.getRange(rowIndex + 1, 1, 1, headersEntrada.length);

        // Atualiza os valores na array para a linha DETALHE
        detailedRow[hEntrada["ROLOS RECEBIDOS"]] = rolosRecebidos;
        detailedRow[hEntrada["KG RECEBIDOS"]] = kgRecebidos;
        detailedRow[hEntrada["STATUS RECEBIMENTO TECIDO"]] = "Recebido no corte"; // Atualiza status da linha detalhe
        detailedRow[hEntrada["DATA REGISTRO"]] = dataRegistro; // Data e Hora do recebimento
        detailedRow[hEntrada["RESPONSÁVEL"]] = usuario;

        // Persistir as alterações na linha DETALHE
        rangeToUpdate.setValues([detailedRow]);
        Logger.log("Linha DETALHE para partida %s atualizada: Rolos: %s, KG: %s, Status: 'Recebido no corte'", idPartida, rolosRecebidos, kgRecebidos);

        // =======================================================
        // LOGGING: Registra o evento de recebimento no 'log_corte'
        // CORREÇÃO APLICADA AQUI: USANDO HLOGCORTE PARA AS COLUNAS DE DESTINO
        // E HENTRADA PARA PEGAR OS VALORES DA LINHA ORIGEM
        // =======================================================
        const novaLinhaLog = headersLogCorte.map(() => ""); // Cria uma linha vazia com base nos cabeçalhos

        novaLinhaLog[hLogCorte["DATA REGISTRO"]] = dataRegistro;
        novaLinhaLog[hLogCorte["TIPO DE ACESSO"]] = "Recebimento"; // Ou "Recebimento - Tecido"
        novaLinhaLog[hLogCorte["USUÁRIO"]] = usuario;
        novaLinhaLog[hLogCorte["MALHARIA"]] = detailedRow[hEntrada["MALHARIA"]];
        novaLinhaLog[hLogCorte["TECIDO"]] = detailedRow[hEntrada["TECIDO"]];
        novaLinhaLog[hLogCorte["COR"]] = detailedRow[hEntrada["COR"]];
        novaLinhaLog[hLogCorte["PRODUTO"]] = detailedRow[hEntrada["PRODUTO"]];
        novaLinhaLog[hLogCorte["ROMANEIO/NF"]] = romaneioCurto;
        novaLinhaLog[hLogCorte["ID PARTIDA"]] = idPartida;
        novaLinhaLog[hLogCorte["ROLOS PARTIDA"]] = rolosRecebidos; // Renomeado no log para 'ROLOS PARTIDA'
        novaLinhaLog[hLogCorte["KG RECEBIDOS"]] = kgRecebidos; // Novo campo para KG Recebidos no log

        // Preencher outros campos do log_corte que você pode ter e queira preencher
        // Eu adicionei GRAMATURA e PESO DOS ROLOS como exemplos, mas você pode ter outros.
        // Verifique seus cabeçalhos do log_corte e os da entrada_destinacao_tecido.
        if (hLogCorte.hasOwnProperty("GRAMATURA") && hEntrada.hasOwnProperty("GRAMATURA")) {
             novaLinhaLog[hLogCorte["GRAMATURA"]] = detailedRow[hEntrada["GRAMATURA"]];
        }
        if (hLogCorte.hasOwnProperty("AFERIÇÃO DE PESO DOS ROLOS") && hEntrada.hasOwnProperty("PESO DOS ROLOS")) {
            novaLinhaLog[hLogCorte["AFERIÇÃO DE PESO DOS ROLOS"]] = detailedRow[hEntrada["PESO DOS ROLOS"]];
        }
        // Exemplo de preenchimento para STATUS, se houver essa coluna no log_corte
        if (hLogCorte.hasOwnProperty("STATUS")) {
            novaLinhaLog[hLogCorte["STATUS"]] = "Recebido";
        }


        abaLogCorte.appendRow(novaLinhaLog);
        Logger.log("Registro adicionado ao log_corte para partida %s. Dados: %s", idPartida, JSON.stringify(novaLinhaLog));
        foundDetailedRow = true;
        break; // Sai do loop interno, já encontrou a partida
      }
    }
    if (!foundDetailedRow) {
      Logger.log("ATENÇÃO: Partida %s do payload não encontrada como linha DETALHE na planilha. Não foi atualizada.", idPartida);
    }
  }

  Logger.log("--- FIM: registrarRecebimentoPartidas ---");
  return { success: true, message: "Recebimento registrado com sucesso!" };
}
// =====================================================================
// 🔍 getDadosEnfesto - Implementação completa:
// Retorna os dados detalhados de uma partida específica (linha DETALHE)
// para a seção de Enfesto e Corte no frontend.
// =====================================================================
function getDadosEnfesto(partidaAlvo) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const h = headersMap(dados[0]);

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const idPartida = (linha[h["ID PARTIDA"]] || "").toString().trim();
    const tipoLinha = (linha[h["TIPO LINHA"]] || "").toString().toUpperCase();

    if (idPartida === partidaAlvo && tipoLinha === "DETALHE") {
      return {
        produto: linha[h["PRODUTO"]] || "N/A",
        cor: linha[h["COR"]] || "N/A",
        malharia: linha[h["MALHARIA"]] || "N/A",
        tecido: (linha[h["TECIDO"]]) || "N/A", // Usar apenas "TECIDO"
        romaneio: linha[h["ROMANEIO"]] || "N/A",
        // 'PCS ESTIMADAS' é o cabeçalho correto para expectativa de PCS (coluna T, índice 19)
        expectativaPCs: linha[h["PCS ESTIMADAS"]] || "N/A",
        rolos: parseInt(linha[h["ROLOS PRINCIPAL"]]) || 0,
        opsCorte: linha[h["OP"]] || "N/A" // Coluna "OP" (AI) para OPs relacionadas
      };
    }
  }
  return null; // Retorna null se a partida não for encontrada
}

// =====================================================================
// 📋 gerarResumoCorte - Implementação completa:
// Recebe os dados do formulário de Enfesto e Corte, processa-os e
// retorna um resumo para o frontend.
// NÃO PERSISTE DADOS AINDA, APENAS PREPARA O RESUMO.
// =====================================================================
function gerarResumoCorte(formData) {
  // formData contém todos os campos do frontend, incluindo os novos
  const {
    idPartida, usuarioCorte, usuarioOutro, obsEnfesto,
    rolosBloqueados, motivosCorte, houveRetalho, numeroVolumes,
    inputRolosEnfestados,
    gradeP, gradeM, gradeG, gradeGG, gradeXG, inputFolhas,
    bateuCorte, tamP, tamM, tamG, tamGG, tamXG,
    inicioCorte, fimCorte
  } = formData;

  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues(); // Buscar todos os dados
  const h = headersMap(dados[0]); // Mapear cabeçalhos

  // Encontrar os dados da partida alvo na planilha
  let produto = "N/A", cor = "N/A", malharia = "N/A", tecido = "N/A",
      romaneio = "N/A", rolosPartidaOriginal = 0;

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const currentIdPartida = (linha[h["ID PARTIDA"]] || "").toString().trim();
    const tipoLinha = (linha[h["TIPO LINHA"]] || "").toString().toUpperCase();

    if (currentIdPartida === idPartida && tipoLinha === "DETALHE") {
      produto = linha[h["PRODUTO"]] || "N/A";
      cor = linha[h["COR"]] || "N/A";
      malharia = linha[h["MALHARIA"]] || "N/A";
      tecido = (linha[h["TECIDO"]]) || "N/A";
      romaneio = linha[h["ROMANEIO"]] || "N/A";
      rolosPartidaOriginal = parseInt(linha[h["ROLOS PRINCIPAL"]]) || 0;
      break; // Encontrou, pode sair do loop
    }
  }

  // Determina o responsável
  const responsavel = (usuarioCorte === "Outro" && usuarioOutro) ? usuarioOutro : usuarioCorte;

  // Calcula peças cortadas e grade informada
  const totalTamanhosGrade = gradeP + gradeM + gradeG + gradeGG + gradeXG;
  const gradeInformada = `${gradeP}P/${gradeM}M/${gradeG}G/${gradeGG}GG/${gradeXG}XG`;
  const pecasEstimadas = totalTamanhosGrade * inputFolhas;

  let pecasCortadasTotal = 0;
  const pecasCortadasPorTamanho = {
    P: 0, M: 0, G: 0, GG: 0, XG: 0
  };

  if (bateuCorte === "sim") {
    pecasCortadasTotal = pecasEstimadas;
    pecasCortadasPorTecasCortadasPorTamanho.P = gradeP * inputFolhas;
    pecasCortadasPorTamanho.M = gradeM * inputFolhas;
    pecasCortadasPorTamanho.G = gradeG * inputFolhas;
    pecasCortadasPorTamanho.GG = gradeGG * inputFolhas;
    pecasCortadasPorTamanho.XG = gradeXG * inputFolhas;
  } else {
    // Se não bateu com a estimativa, usa os valores manuais
    pecasCortadasPorTamanho.P = tamP;
    pecasCortadasPorTamanho.M = tamM;
    pecasCortadasPorTamanho.G = tamG;
    pecasCortadasPorTamanho.GG = tamGG;
    pecasCortadasPorTamanho.XG = tamXG;
    pecasCortadasTotal = tamP + tamM + tamG + tamGG + tamXG;
  }

  return {
    partida: idPartida,
    produto,
    cor,
    malharia,
    tecido,
    romaneio,
    rolosPartidaOriginal,
    responsavel,
    observacoes: obsEnfesto,
    rolosEnfestados: inputRolosEnfestados,
    rolosBloqueados: rolosBloqueados, // Novo campo
    motivosCorte: motivosCorte,      // Novo campo
    houveRetalho: houveRetalho,      // Novo campo
    numeroVolumes: numeroVolumes,    // Novo campo
    gradeInformada,
    numeroFolhas: inputFolhas,
    corteBateu: bateuCorte,
    pecasCortadasTotal,
    pecasCortadasPorTamanho,
    inicioCorte: new Date(inicioCorte).toISOString(),
    fimCorte: new Date(fimCorte).toISOString()
  };
}


// =====================================================================
// ✅ finalizarCorteEnfesto - Implementação completa:
// Registra o corte final. Atualiza a aba "entrada_destinacao_tecido"
// e registra uma nova linha no "log_corte" com todos os detalhes.
// =====================================================================
function finalizarCorteEnfesto(resumoCorte) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const abaLog = ss.getSheetByName("log_corte");

  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const hEntrada = headersMap(dadosEntrada[0]);

  const now = Utilities.formatDate(new Date(), Session.getScriptTimeZone(), "dd/MM/yyyy HH:mm:ss"); // Adicionado segundos para mais precisão

  // 1. Atualizar STATUS CORTE na aba "entrada_destinacao_tecido"
  let linhaAtualizada = false;
  for (let i = 1; i < dadosEntrada.length; i++) {
    const linha = dadosEntrada[i];
    const idPartida = (linha[hEntrada["ID PARTIDA"]] || "").toString().trim();
    const tipoLinha = (linha[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();

    if (idPartida === resumoCorte.partida && tipoLinha === "DETALHE") {
      // +1 para o índice da coluna pois getRange é 1-based
      abaEntrada.getRange(i + 1, hEntrada["STATUS CORTE"] + 1).setValue("Cortado");
      abaEntrada.getRange(i + 1, hEntrada["FIM DO CORTE"] + 1).setValue(new Date(resumoCorte.fimCorte));
      abaEntrada.getRange(i + 1, hEntrada["INICIO CORTE"] + 1).setValue(new Date(resumoCorte.inicioCorte)); // Adicionar inicioCorte
      abaEntrada.getRange(i + 1, hEntrada["ROLOS ENFESTADOS"] + 1).setValue(resumoCorte.rolosEnfestados); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["ROLOS BLOQUEADOS"] + 1).setValue(resumoCorte.rolosBloqueados); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["MOTIVOS"] + 1).setValue(resumoCorte.motivosCorte); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["RETALHOS?"] + 1).setValue(resumoCorte.houveRetalho); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["NUMERO DE VOLUMES"] + 1).setValue(resumoCorte.numeroVolumes); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["FOLHAS"] + 1).setValue(resumoCorte.numeroFolhas); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["QUANTIDADE CORTADA"] + 1).setValue(resumoCorte.pecasCortadasTotal); // Novo campo
      abaEntrada.getRange(i + 1, hEntrada["QUANTIDADE CORTADA POR TAMANHO"] + 1).setValue(
          `P:${resumoCorte.pecasCortadasPorTamanho.P}, M:${resumoCorte.pecasCortadasPorTamanho.M}, G:${resumoCorte.pecasCortadasPorTamanho.G}, GG:${resumoCorte.pecasCortadasPorTamanho.GG}, XG:${resumoCorte.pecasCortadasPorTamanho.XG}`
      ); // Novo campo

      // Atualizar a grade na entrada_destinacao_tecido (se houver essa coluna lá)
      if (hEntrada.hasOwnProperty("GRADE")) {
          abaEntrada.getRange(i + 1, hEntrada["GRADE"] + 1).setValue(resumoCorte.gradeInformada);
      }
      if (hEntrada.hasOwnProperty("QUANTIDADE DE TAMANHOS")) {
          // Calcula a quantidade de tamanhos a partir da grade
          const totalTamanhosGrade = Object.values(resumoCorte.pecasCortadasPorTamanho).reduce((acc, val) => acc + val, 0);
          abaEntrada.getRange(i + 1, hEntrada["QUANTIDADE DE TAMANHOS"] + 1).setValue(totalTamanhosGrade);
      }
      
      linhaAtualizada = true;
      break;
    }
  }

  if (!linhaAtualizada) {
    throw new Error(`Erro: Partida ${resumoCorte.partida} não encontrada para atualização na entrada_destinacao_tecido.`);
  }

  // 2. Registrar no log_corte
  const logHeaders = abaLog.getDataRange().getValues()[0];
  const hLog = headersMap(logHeaders);
  const logRow = new Array(logHeaders.length).fill(""); // Cria uma linha vazia com o tamanho correto

  // Preenchendo a linha do log com base no resumoCorte e mapeamento de cabeçalhos
  logRow[hLog["DATA REGISTRO"]] = now;
  logRow[hLog["TIPO DE ACESSO"]] = "Corte e Enfesto";
  logRow[hLog["USUÁRIO"]] = resumoCorte.responsavel;
  logRow[hLog["MALHARIA"]] = resumoCorte.malharia;
  logRow[hLog["TECIDO"]] = resumoCorte.tecido;
  logRow[hLog["COR"]] = resumoCorte.cor;
  logRow[hLog["PRODUTO"]] = resumoCorte.produto;
  logRow[hLog["ROMANEIO/NF"]] = resumoCorte.romaneio;
  logRow[hLog["ID PARTIDA"]] = resumoCorte.partida;
  
  // Detalhes do Corte e Enfesto
  logRow[hLog["NUM DE ROLOS ENFESTADOS"]] = resumoCorte.rolosEnfestados;
  logRow[hLog["ROLOS BLOQUEADOS"]] = resumoCorte.rolosBloqueados;
  logRow[hLog["MOTIVOS"]] = resumoCorte.motivosCorte;
  logRow[hLog["RETALHOS?"]] = resumoCorte.houveRetalho;
  logRow[hLog["NUMERO DE VOLUMES"]] = resumoCorte.numeroVolumes;
  logRow[hLog["GRADE"]] = resumoCorte.gradeInformada;
  logRow[hLog["QUANTIDADE DE TAMANHOS"]] = Object.values(resumoCorte.pecasCortadasPorTamanho).reduce((acc, val) => acc + val, 0); // Soma das quantidades cortadas
  logRow[hLog["FOLHAS"]] = resumoCorte.numeroFolhas;
  logRow[hLog["QUANTIDADE CORTADA"]] = resumoCorte.pecasCortadasTotal;
  logRow[hLog["QUANTIDADE CORTADA POR TAMANHO"]] = 
      `P:${resumoCorte.pecasCortadasPorTamanho.P}, M:${resumoCorte.pecasCortadasPorTamanho.M}, G:${resumoCorte.pecasCortadasPorTamanho.G}, GG:${resumoCorte.pecasCortadasPorTamanho.GG}, XG:${resumoCorte.pecasCortadasPorTamanho.XG}`;
  logRow[hLog["INICIO CORTE"]] = new Date(resumoCorte.inicioCorte); // Salvar como objeto Date para manter formato de data/hora
  logRow[hLog["FIM DO CORTE"]] = new Date(resumoCorte.fimCorte);   // Salvar como objeto Date

  // Outros campos do log_corte que podem ser preenchidos ou deixar vazios
  // Ex: logRow[hLog["GRAMATURA"]] = detailedRow[hEntrada["GRAMATURA"]]; // Se quiser replicar a gramatura da linha de entrada
  // Ex: logRow[hLog["AFERIÇÃO DE PESO DOS ROLOS"]] = ...; 
  // Ex: logRow[hLog["STATUS"]] = "Concluído"; 
  // Ex: logRow[hLog["OP"]] = detailedRow[hEntrada["OP"]]; // Se a OP estiver na linha de entrada detalhe

  // Calcular e registrar 'CÁLCULO DE ROLOS' (AD) no log_corte
  // A diferença entre rolos recebidos na partida, rolos bloqueados e rolos enfestados
  let rolosRecebidosNaPartida = 0;
  for (let i = 1; i < dadosEntrada.length; i++) {
      const linha = dadosEntrada[i];
      const idPartida = (linha[hEntrada["ID PARTIDA"]] || "").toString().trim();
      if (idPartida === resumoCorte.partida && (linha[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase() === "DETALHE") {
          rolosRecebidosNaPartida = parseInt(linha[hEntrada["ROLOS RECEBIDOS"]] || 0); // Pega os rolos efetivamente recebidos da partida
          break;
      }
  }
  const calculoRolos = rolosRecebidosNaPartida - resumoCorte.rolosBloqueados - resumoCorte.rolosEnfestados;
  if (hLog.hasOwnProperty("CALCULO DE ROLOS")) {
      logRow[hLog["CALCULO DE ROLOS"]] = calculoRolos;
  }
  
  // COMPROVANTE E DECISÃO - TIPO 3 (AH)
  // Assumindo que este campo é para exibir um resumo da ação final
  if (hLog.hasOwnProperty("COMPROVANTE E DECISÃO- TIPO 3")) {
      logRow[hLog["COMPROVANTE E DECISÃO- TIPO 3"]] = `Corte de Partida ${resumoCorte.partida} finalizado por ${resumoCorte.responsavel} em ${now}. Total Peças: ${resumoCorte.pecasCortadasTotal}. Rolos Enfestados: ${resumoCorte.rolosEnfestados}. Rolos Bloqueados: ${resumoCorte.rolosBloqueados}.`;
  }

  // OPS EM CORTE (AI)
  // Você já tem essa informação em `getDadosEnfesto` como `opsCorte`,
  // e deveria ter sido persistida no `resumoCorte` se necessário.
  // Se não estiver no `resumoCorte`, você precisaria buscar novamente na planilha.
  // Para simplificar, vou assumir que `opsCorte` pode ser adicionado ao resumoCorte.
  // Ou, se a coluna 'OP' existe na entrada_destinacao_tecido e no log, podemos copiá-la.
  if (hLog.hasOwnProperty("OPS EM CORTE")) { // Supondo que o cabeçalho seja "OPS EM CORTE" no log
      let opsVinculadasString = "";
      for (let i = 1; i < dadosEntrada.length; i++) {
        const linha = dadosEntrada[i];
        const idPartida = (linha[hEntrada["ID PARTIDA"]] || "").toString().trim();
        const tipoLinha = (linha[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();
        if (idPartida === resumoCorte.partida && tipoLinha === "DETALHE") {
          opsVinculadasString = (linha[hEntrada["OP"]] || "").toString().trim();
          break;
        }
      }
      logRow[hLog["OPS EM CORTE"]] = opsVinculadasString;
  }


  abaLog.appendRow(logRow);
  Logger.log("Registro de corte e enfesto adicionado ao log_corte para partida %s. Dados: %s", resumoCorte.partida, JSON.stringify(logRow));

  return `Partida ${resumoCorte.partida} finalizada com sucesso!`;
}


// ===========================================================
// 🔄 Retorna as partidas pendentes de um romaneio para recebimento
// ===========================================================
function getPartidasPorRomaneio(romaneioSelecionado) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("entrada_destinacao_tecido");
  const data = sheet.getDataRange().getValues();
  const hEntrada = headersMap(data[0]);

  const partidas = [];

  // Extrai só o número do romaneio (antes do traço ou espaço)
  const romaneioLimpo = romaneioSelecionado.split(" -")[0].trim();

  for (let i = 1; i < data.length; i++) {
    const row = data[i];
    const tipoLinha = (row[hEntrada["TIPO LINHA"]] || "").toString().trim().toUpperCase();
    const romaneio = (row[hEntrada["ROMANEIO"]] || "").toString().trim();
    const statusReceb = (row[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().trim().toUpperCase();

    if (
      tipoLinha === "DETALHE" &&
      romaneio === romaneioLimpo &&
      !statusReceb.includes("RECEBIDO NO CORTE")
    ) {
      partidas.push({
        id: row[hEntrada["ID PARTIDA"]],
        produto: row[hEntrada["PRODUTO"]],
        cor: row[hEntrada["COR"]],
        pendentes: row[hEntrada["TOTAL ROLOS"]],
        recebidos: row[hEntrada["CORTE"]] || 0,
        kgRecebidos: row[hEntrada["TOTAL KG"]] || 0
      });
    }
  }

  return partidas;
}


// ============== FUNÇÕES AUXILIARES E PLACEHOLDERS (Ajustadas) ==============

// Estas funções foram ajustadas para retornar dados mais realistas para fins de teste,
// mas se você já as possui em outro lugar ou as integrará a um banco de dados,
// mantenha suas implementações originais.

function getPartidasDisponiveisParaPesagem(romaneio) {
  Logger.log(`[BACKEND] Chamada para getPartidasDisponiveisParaPesagem com romaneio: ${romaneio}`);
  // Implemente a lógica real para buscar partidas que ainda não foram pesadas
  // e pertencem ao romaneio especificado.
  // Exemplo: Buscar linhas DETALHE para o romaneio que não tenham peso registrado.
  return ["PARTIDA_001", "PARTIDA_002"]; // Dados de exemplo
}
function registrarPesagem(payload) {
  Logger.log(`[BACKEND] Chamada para registrarPesagem com payload: ${JSON.stringify(payload)}`);
  // Implemente a lógica real para registrar a pesagem na sua planilha.
  // Isso pode envolver:
  // 1. Encontrar a linha DETALHE correspondente à `payload.partida`.
  // 2. Preencher uma coluna de "GRAMATURA REAL" com `payload.gramatura`.
  // 3. Preencher uma coluna de "PESOS DOS ROLOS" com `payload.pesos` (pode ser uma string JSON).
  // 4. Atualizar um status se necessário (ex: "Pesado").
  return "Pesagem registrada com sucesso no backend.";
}

function forcarRecebimentoPorRomaneio(romaneio) {
  Logger.log(`[BACKEND] Chamada para forcarRecebimentoPorRomaneio com romaneio: ${romaneio}`);
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const h = headersMap(dados[0]);
  const now = Utilities.formatDate(new Date(), Session.getScriptTimeZone(), "dd/MM/yyyy HH:mm");
  let linhasAtualizadas = 0;

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const romaneioAtual = (linha[h["ROMANEIO"]] || "").toString().trim();
    const tipo = (linha[h["TIPO LINHA"]] || "").toString().toUpperCase();
    const statusRecebimento = (linha[h["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();
    const statusCorte = (linha[h["STATUS CORTE"]] || "").toString().toUpperCase();

    if (romaneioAtual === romaneio) {
      if (tipo === "DETALHE" && !statusCorte.includes("RECEBIDO NO CORTE")) {
        aba.getRange(i + 1, h["STATUS CORTE"] + 1).setValue("Tecido Recebido");
        aba.getRange(i + 1, h["CHECK DE RECEBIMENTO"] + 1).setValue(now);
        linhasAtualizadas++;
      } else if (tipo === "MÃE" && !statusRecebimento.includes("TECIDO RECEBIDO")) {
        aba.getRange(i + 1, h["STATUS RECEBIMENTO TECIDO"] + 1).setValue("Recebido no Corte");
        aba.getRange(i + 1, h["DATA"] + 1).setValue(now);
      }
    }
  }
  return `Forçado recebimento para ${linhasAtualizadas} linhas de detalhe no romaneio ${romaneio}.`;
}

function getResumoPainel() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const entrada = ss.getSheetByName("entrada_destinacao_tecido");
  const log = ss.getSheetByName("log_corte");

  const entradaData = entrada.getDataRange().getValues();
  const hEntrada = headersMap(entradaData[0]);

  let totalRolosRecebidos = 0;
  let totalRolosAguardandoRecebimento = 0;
  let totalRolosProntosParaCorte = 0;

  for (let i = 1; i < entradaData.length; i++) {
    const linha = entradaData[i];
    const tipoLinha = (linha[hEntrada["TIPO LINHA"]] || "").toString().toUpperCase();
    const statusReceb = (linha[hEntrada["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();
    const statusCorte = (linha[hEntrada["STATUS CORTE"]] || "").toString().toUpperCase();
    const rolos = parseInt(linha[hEntrada["ROLOS RECEBIDOS"]]) || parseInt(linha[hEntrada["ROLOS PRINCIPAL"]]) || 0;

    if (tipoLinha === "DETALHE") {
      if (statusReceb.includes("RECEBIDO NO CORTE")) totalRolosRecebidos += rolos;
      if (!statusReceb.includes("RECEBIDO")) totalRolosAguardandoRecebimento += rolos;
      if (statusReceb.includes("RECEBIDO") && !statusCorte.includes("CORTADO")) totalRolosProntosParaCorte += rolos;
    }
  }

  const logData = log.getDataRange().getValues();
  const hLog = headersMap(logData[0]);

  let totalRolosCortados = 0;
  for (let i = 1; i < logData.length; i++) {
    const linha = logData[i];
    const tipoAcesso = (linha[hLog["TIPO DE ACESSO"]] || "").toString().toUpperCase();
const rolosEnfestados = parseInt(linha[hLog["NUM DE ROLOS ENFESTADOS"]]) || 0;
const fimEnfesto = linha[hLog["FIM DO ENFESTO"]];

if (tipoAcesso === "ENFESTO + CORTE" && rolosEnfestados > 0 && fimEnfesto) {
  totalRolosCortados += rolosEnfestados;
}

  }

  let rolosAguardandoCorte = Math.max(0, totalRolosProntosParaCorte - totalRolosCortados);

  return {
    rolosRecebidosCorte: totalRolosRecebidos,
    rolosEnfestadosCortados: totalRolosCortados,
    rolosAguardandoCorte: rolosAguardandoCorte,
    rolosAguardandoRecebimento: totalRolosAguardandoRecebimento
  };
}


// =====================================================================
// 👤 getUserEmail - Retorna o e-mail do usuário logado
// Utilizado pelo frontend para preencher campos de responsável.
// =====================================================================
function getUserEmail() {
  const email = Session.getActiveUser().getEmail();
  Logger.log("E-mail do usuário logado: %s", email);
  return email;
}


function getPartidasDisponiveisParaEnfesto() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  if (!aba) return [];

  const dados = aba.getDataRange().getValues();
  const headers = dados[0].map(h => h.toString().toUpperCase());

  // Índices das colunas relevantes
  const idxTipo = headers.indexOf("TIPO LINHA");
  const idxStatus = headers.indexOf("STATUS CORTE");
  const idxProduto = headers.indexOf("PRODUTO");
  const idxMalharia = headers.indexOf("MALHARIA");
  const idxTecido = headers.indexOf("TECIDO");
  const idxCor = headers.indexOf("COR");
  const idxPartida = headers.indexOf("ID PARTIDA");
  const idxRomaneio = headers.indexOf("ROMANEIO");
  const idxGrade = headers.indexOf("GRADE");
  const idxEstimativa = headers.indexOf("PCS ESTIMADAS");
  const idxFolhas = headers.indexOf("FOLHAS");

  const lista = [];

  for (let i = 1; i < dados.length; i++) {
    const l = dados[i];
    const tipo = (l[idxTipo] || "").toString().toUpperCase();
    const status = (l[idxStatus] || "").toString().toUpperCase();

    // Filtra apenas linhas do tipo "DETALHE" com status "TECIDO RECEBIDO"
    if (tipo !== "DETALHE") continue;
    if (status !== "TECIDO RECEBIDO") continue;

    lista.push({
      partida: l[idxPartida] || "",
      produto: l[idxProduto] || "",
      malharia: l[idxMalharia] || "",
      tecido: l[idxTecido] || "",
      cor: l[idxCor] || "",
      romaneio: l[idxRomaneio] || "",
      grade: l[idxGrade] || "",
      estimativa: l[idxEstimativa] || "",
      folhas: l[idxFolhas] || ""
    });
  }

  return lista;
}



// ✅ Centraliza toda atualização de status de corte
function atualizarStatusCorte(idPartida, novoStatus) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const idxIdPartida = dados[0].indexOf("ID Partida");
  const idxStatus = dados[0].indexOf("Status Corte");

  for (let i = 1; i < dados.length; i++) {
    if ((dados[i][idxIdPartida] || "").toString().trim() === idPartida) {
      aba.getRange(i + 1, idxStatus + 1).setValue(novoStatus);
      break;
    }
  }
}

// ✅ Script para preencher retroativamente entradas como "Recebido no Corte" e "Cortado" com base em datas de romaneio até 30/05
// Requisitos:
// ✅ Função auxiliar para mapear cabeçalhos
function headersMap(headerRow) {
  const map = {};
  for (let i = 0; i < headerRow.length; i++) {
    const nome = headerRow[i]?.toString().trim().toUpperCase();
    if (nome) map[nome] = i;
  }
  return map;
}

// ✅ Script retroativo para registrar recebimentos, cortes, alocação de confecção e log até 18/06/2025
function retroagirRecebimentosECortes() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const log = ss.getSheetByName("log_corte");
  const dados = aba.getDataRange().getValues();
  const h = headersMap(dados[0]);
  const hoje = new Date();
  const corteLimite = new Date("2025-06-18T23:59:59");

  let countRecebidos = 0;
  let countCortados = 0;
  let countLogGerado = 0;
  let countConfAlocada = 0;

  const colReceb = h["STATUS RECEBIMENTO TECIDO"];
  const colRegistro = h["DATA REGISTRO"];
  const colStatusCorte = h["STATUS CORTE"];
  const colFimCorte = h["ENTREGA CONFECÇÃO"];
  const colConfec = h["CONFECÇÃO"];
  const colProduto = h["PRODUTO"];
  const colCor = h["COR"];
  const colTecido = h["TECIDO"];
  const colPartida = h["ID PARTIDA"];
  const colRomaneio = h["ROMANEIO/NF"];
  const colTipo = h["TIPO LINHA"];
  const colDataEnvio = h["DATA ENVIO"];

  if ([colReceb, colRegistro, colStatusCorte, colFimCorte, colProduto, colCor, colTecido, colPartida, colTipo, colDataEnvio].includes(undefined)) {
    Logger.log("🔍 Cabeçalhos disponíveis:", h);
    throw new Error("❌ Algumas colunas obrigatórias não foram encontradas. Confira nomes e acentuação.");
  }

  const dadosLog = log.getDataRange().getValues();
  const logHeader = headersMap(dadosLog[0]);

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const tipo = (linha[colTipo] || "").toString().toUpperCase();
    const statusReceb = (linha[colReceb] || "").toString().toUpperCase();
    const statusCorte = (linha[colStatusCorte] || "").toString().toUpperCase();
    const dataEnvio = linha[colDataEnvio];

    // RECEBIMENTO
    if (tipo === "MÃE" && !statusReceb.includes("RECEBIDO")) {
      aba.getRange(i + 1, colReceb + 1).setValue("Recebido no corte");
      aba.getRange(i + 1, colRegistro + 1).setValue(hoje);
      countRecebidos++;
    }

    // CORTE + LOG + ALOCAÇÃO
    if (tipo === "DETALHE" && !statusCorte.includes("CORTADO") && dataEnvio instanceof Date && dataEnvio <= corteLimite) {
      aba.getRange(i + 1, colStatusCorte + 1).setValue("Cortado");
      aba.getRange(i + 1, colFimCorte + 1).setValue(hoje);
      countCortados++;

      // Confecção sugerida com base em nome parcial do produto
      const sugestaoConf = linha[colProduto]?.toString().includes("FEM") ? "Costura FEM" : "Costura MASC";
      if (!linha[colConfec]) {
        aba.getRange(i + 1, colConfec + 1).setValue(sugestaoConf);
        countConfAlocada++;
      }

      // Geração de log sem duplicar
      const partida = linha[colPartida]?.toString();
      const produto = linha[colProduto];
      const cor = linha[colCor];
      const tecido = linha[colTecido];
      const romaneio = linha[colRomaneio];
      const jaExiste = dadosLog.some(l => l[logHeader["ID PARTIDA"]]?.toString() === partida);

      if (!jaExiste && partida) {
        log.appendRow([
          new Date(), "Retroativo", "sistema", "",
          tecido, cor, produto, romaneio,
          "", "", "", "", "", "", "", "", "", "", "",
          partida, "", "", "", "", "", ""
        ]);
        countLogGerado++;
      }
    }
  }

  Logger.log(`✔️ ${countRecebidos} recebimentos, ${countCortados} cortes, ${countConfAlocada} alocações, ${countLogGerado} logs gerados.`);
  return `✔️ Retroativo completo até 18/06: ${countRecebidos} recebidos | ${countCortados} cortados | ${countConfAlocada} confecções atribuídas | ${countLogGerado} logs inseridos.`;
}

function debugResumoPainel() {
  const resumo = getResumoPainel();
  Logger.log("📊 RESUMO ATUALIZADO:");
  Logger.log("Rolos Recebidos: " + resumo.rolosRecebidosCorte);
  Logger.log("Rolos Enfestados & Cortados: " + resumo.rolosEnfestadosCortados);
  Logger.log("Rolos Aguardando Corte: " + resumo.rolosAguardandoCorte);
  Logger.log("Rolos Aguardando Recebimento: " + resumo.rolosAguardandoRecebimento);
}



function getResumoRomaneiosPendentes() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const entrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = entrada.getDataRange().getValues();
  const h = headersMap(dados[0]);

  const resultado = {}; // agrupado por malharia

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const tipoLinha = (linha[h["TIPO LINHA"]] || "").toString().toUpperCase();
    const statusReceb = (linha[h["STATUS RECEBIMENTO TECIDO"]] || "").toString().toUpperCase();

    if (tipoLinha === "DETALHE" && !statusReceb.includes("RECEBIDO")) {
      const malharia = linha[h["MALHARIA"]] || "Sem Malharia";
      const romaneio = linha[h["ROMANEIO/NF"]] || "SEM ROMANEIO";
      const rolos = parseInt(linha[h["ROLOS PRINCIPAL"]]) || 0;

      if (!resultado[malharia]) {
        resultado[malharia] = {
          totalRolos: 0,
          romaneios: new Set()
        };
      }

      resultado[malharia].totalRolos += rolos;
      resultado[malharia].romaneios.add(romaneio);
    }
  }

  return Object.entries(resultado).map(([malharia, dados]) => ({
    malharia,
    totalRolos: dados.totalRolos,
    totalRomaneios: dados.romaneios.size
  }));
}

function registrarCorteCompleto(resumo) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLogCorte = ss.getSheetByName("log_corte");
  const abaDestino = ss.getSheetByName("entrada_destinacao_tecido");

  const dados = abaLogCorte.getDataRange().getValues();
  const romaneioBuscado = resumo.romaneio;
  let linhaEncontrada = -1;

  for (let i = 1; i < dados.length; i++) {
    const romaneio = dados[i][7];
    if (romaneio && romaneio.toString().trim() === romaneioBuscado.toString().trim()) {
      linhaEncontrada = i + 1;
      break;
    }
  }

  if (linhaEncontrada === -1) {
    throw new Error(`❌ Romaneio ${romaneioBuscado} não encontrado no log_corte.`);
  }

  const usuario = Session.getActiveUser().getEmail() || "Painel Corte";
  const dataRegistro = new Date();

  const atualizacoes = [
    [0, dataRegistro], [1, "Enfesto + Corte"], [2, usuario],
    [3, resumo.malharia || ""], [4, resumo.tecido || ""], [5, resumo.cor || ""],
    [6, resumo.produto || ""], [7, resumo.romaneio || ""], [8, "conforme"],
    [9, "Não"], [10, "✅ Enfesto + Corte registrado"],
    [13, resumo.rolosTotal || ""], [15, resumo.idPartida || ""],
    [16, resumo.rolosPartida || ""], [17, "✅ Enfesto + Corte registrado"],
    [20, resumo.resumoEstimativa || ""], [22, usuario],
    [23, resumo.inicioCorte || dataRegistro], [24, resumo.rolosEnfestados || ""],
    [25, resumo.rolosBloqueados || 0], [26, resumo.motivoBloqueio || ""],
    [27, resumo.calculoRolos || ""], [28, resumo.numFolhas || ""],
    [29, resumo.fimCorte || dataRegistro], [30, resumo.inicioCorte || dataRegistro],
    [31, resumo.gradeString || ""], [32, resumo.quantidadeTamanhos || ""],
    [33, resumo.folhas || ""], [34, resumo.retaliaOuNao || "Não"],
    [35, resumo.totalCortado || ""], [36, JSON.stringify(resumo.grade || {})],
    [37, "✅ Enfesto + Corte registrado"], [38, resumo.totalCortado || ""],
    [39, JSON.stringify(resumo.grade || {})], [40, "OK"], [41, "✅"],
    [42, resumo.numeroDeVolumes || ""], [43, resumo.resumoDeVolumes || ""],
    [44, "✅"]
  ];

  atualizacoes.forEach(([col, val]) => {
    abaLogCorte.getRange(linhaEncontrada, col + 1).setValue(val);
  });

  // Atualiza na entrada_destinacao_tecido (AJ = 36, AK = 37)
  const dadosDestino = abaDestino.getDataRange().getValues();
  for (let j = 1; j < dadosDestino.length; j++) {
    const linha = dadosDestino[j];
    if (
      linha[0]?.toString().trim() === resumo.produto?.toString().trim() &&
      linha[1]?.toString().trim() === resumo.cor?.toString().trim() &&
      linha[2]?.toString().trim() === resumo.tamanho?.toString().trim() &&
      linha[5]?.toString().trim() === resumo.tecido?.toString().trim() &&
      linha[6]?.toString().trim() === resumo.malharia?.toString().trim()
    ) {
      abaDestino.getRange(j + 1, 36).setValue("✅ Enfesto + Corte registrado");
      abaDestino.getRange(j + 1, 37).setValue(dataRegistro);
    }
  }
}


Os cortes estando prontos> vão para as confecções

<!-- painelLogistica.html | Painel de Logística Orbitta x Berzerk -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>🚚 Painel de Logística - Orbitta x Berzerk</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Poppins', sans-serif; }
    .resumo-box {
      background-color: #ebf8ff;
      border: 1px solid #bee3f8;
      border-radius: 0.5rem;
      padding: 1rem;
      margin-top: 1rem;
      font-size: 0.875rem;
      color: #2a4365;
    }
  </style>
</head>
<body class="bg-gray-100 p-6">
  <div class="max-w-6xl mx-auto bg-white p-6 shadow-xl rounded-xl space-y-8">
    <h1 class="text-3xl font-bold text-center">🚚 Painel de Logística - Orbitta x Berzerk</h1>

    <!-- 🔀 Seletor de Modo de Movimentação -->
    <div>
      <label class="block mb-2 font-semibold">🔀 Selecione o tipo de movimentação:</label>
      <select id="modoLogistica" class="w-full p-2 border rounded" onchange="carregarDadosLogistica()">
        <option value="">Selecione...</option>
        <option value="retiradaCorte">1️⃣ Retirada de Corte + Entrega nas Confecções</option>
        <option value="retornoConf">2️⃣ Retirada de Produto + Entrega na Berzerk</option>
      </select>
    </div>

    <!-- 🔁 Bloco de Resumo -->
    <div id="blocoResumo" class="hidden">
      <div id="resumoConteudo" class="resumo-box"></div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
        <input type="date" id="dataRetirada" class="p-2 border rounded" placeholder="Data Retirada Real">
        <input type="date" id="dataEntrega" class="p-2 border rounded" placeholder="Data Entrega Real">
        <input type="text" id="nomeMotorista" class="p-2 border rounded" placeholder="Nome do Motorista">
      </div>

      <button onclick="confirmarMovimentacaoLogistica()" class="mt-6 bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700">
        ✅ Confirmar Movimentação
      </button>
    </div>
  </div>

  <script>
    // 🌐 Função principal ao mudar o modo
    function carregarDadosLogistica() {
      const modo = document.getElementById("modoLogistica").value;
      if (!modo) return;

      google.script.run.withSuccessHandler(exibirResumoLogistica).getLogisticaDoDia(modo);
    }

    // 🧾 Exibe resumo visual da OP + confecção + rota
    function exibirResumoLogistica(dados) {
      const bloco = document.getElementById("blocoResumo");
      const conteudo = document.getElementById("resumoConteudo");
      if (!dados || dados.length === 0) {
        conteudo.innerHTML = "<p class='text-red-600'>Nenhuma movimentação prevista para hoje.</p>";
        bloco.classList.remove("hidden");
        return;
      }

      let html = "";
      dados.forEach((item, i) => {
        html += `<p><strong>OP:</strong> ${item.op} | <strong>Produto:</strong> ${item.produto} | <strong>Cor:</strong> ${item.cor}</p>`;
        html += `<p><strong>Qtd Cortada:</strong> ${item.qtd} | <strong>Volumes:</strong> ${item.volumes}</p>`;
        html += `<p><strong>Confecção:</strong> ${item.confeccao} | <strong>Endereço:</strong> ${item.endereco}</p>`;
        html += `<p><strong>Rota:</strong> ${item.rota}</p><hr class='my-2'>`;
      });
      conteudo.innerHTML = html;
      bloco.classList.remove("hidden");
    }

    // 📝 Confirma e registra a movimentação no backend
    function confirmarMovimentacaoLogistica() {
      const modo = document.getElementById("modoLogistica").value;
      const retirada = document.getElementById("dataRetirada").value;
      const entrega = document.getElementById("dataEntrega").value;
      const motorista = document.getElementById("nomeMotorista").value;

      if (!retirada || !entrega || !motorista) {
        alert("Preencha todos os campos antes de confirmar.");
        return;
      }

      const payload = {
        modo: modo,
        dataRetirada: retirada,
        dataEntrega: entrega,
        motorista: motorista
      };

      google.script.run.withSuccessHandler(() => {
        alert("✅ Movimentação registrada com sucesso!");
        location.reload();
      }).registrarMovimentacaoLogistica(payload);
    }
  </script>
</body>
</html>

// 📦 backendLogistica.gs | Painel de Logística - Orbitta x Berzerk

// ======================================================================
// 1️⃣ Função principal: retorna dados logísticos do dia (por modo)
// ======================================================================
function getLogisticaDoDia(modo) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaCorte = ss.getSheetByName('log_corte');
  const abaFornecimento = ss.getSheetByName('matriz_fornecimento');
  const hoje = new Date();
  hoje.setHours(0, 0, 0, 0);

  const dadosCorte = abaCorte.getDataRange().getValues();
  const dados = [];

  for (let i = 1; i < dadosCorte.length; i++) {
    const linha = dadosCorte[i];
    const dataCorte = linha[34]; // AI
    const qtdCortada = linha[40]; // AO
    const volumes = linha[47]; // AV
    const op = linha[1];
    const produto = linha[4];
    const cor = linha[6];
    const confeccao = linha[41]; // AP (Confecção)

    if (!dataCorte || !confeccao || !op) continue;

    const dataPrevista = new Date(dataCorte);
    dataPrevista.setDate(dataPrevista.getDate() + 1);
    dataPrevista.setHours(0, 0, 0, 0);

    if (modo === 'retiradaCorte' && +dataPrevista === +hoje) {
      const endereco = buscarEnderecoConfeccao(abaFornecimento, confeccao);
      dados.push({ produto, cor, op, qtd: qtdCortada, volumes, confeccao, endereco, rota: gerarRota(endereco) });
    }
  }

  return dados;
}

// ======================================================================
// 2️⃣ Busca o endereço da confecção a partir da matriz
// ======================================================================
function buscarEnderecoConfeccao(aba, nomeConf) {
  const dados = aba.getDataRange().getValues();
  for (let i = 1; i < dados.length; i++) {
    if (String(dados[i][0]).trim().toLowerCase() === String(nomeConf).trim().toLowerCase()) {
      return dados[i][1]; // Supondo que endereço está na coluna B
    }
  }
  return 'Endereço não encontrado';
}

// ======================================================================
// 3️⃣ Gera uma rota simples com base no endereço (placeholder)
// ======================================================================
function gerarRota(enderecoDestino) {
  const origem = "Av. Maria Coelho Aguiar, 573 - São Paulo";
  return `${origem} → ${enderecoDestino}`;
}

// ======================================================================
// 4️⃣ Registra movimentação na aba log_logística e entrada_destinacao_tecido
// ======================================================================
function registrarMovimentacaoLogistica(payload) {
  const { modo, dataRetirada, dataEntrega, motorista } = payload;
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName('log_logística');
  const abaTecido = ss.getSheetByName('entrada_destinacao_tecido');
  const dadosDia = getLogisticaDoDia(modo);
  const dataRegistro = new Date();

  dadosDia.forEach(item => {
    const linha = [
      dataRegistro,
      modo,
      motorista,
      item.op,
      item.produto,
      item.cor,
      item.qtd,
      item.volumes,
      item.confeccao,
      item.endereco,
      dataRetirada,
      dataEntrega,
      item.rota
    ];
    abaLog.appendRow(linha);

    if (modo === 'retornoConf') {
      // Atualiza a aba de entrada_destinacao_tecido com retorno real
      const dadosTecido = abaTecido.getDataRange().getValues();
      for (let i = 1; i < dadosTecido.length; i++) {
        if (dadosTecido[i][29] === item.op) { // Coluna AD = OP
          abaTecido.getRange(i + 1, 39).setValue(dataEntrega); // Coluna AM = Retorno Confecção
          break;
        }
      }
    }
  });
}


// ======================================================================
// 🚀 doGet: renderiza o painelLogistica.html
// ======================================================================
function doGet(e) {
  const painel = "painelLogistica"; // nome exato do arquivo HTML sem .html
  const template = HtmlService.createTemplateFromFile(painel);
  return template.evaluate().setTitle("Painel de Logística").setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}


a logística leva esse corte até a confecção e deve aguardar agendamento para buscar e entregar o corte no estoque da berzerk

// ✅ Correção definitiva backendConfeccao.gs com suporte a nomes com acento

function doGet(e) {
  const template = HtmlService.createTemplateFromFile("painelConfeccao");
  return template.evaluate().setTitle("Painel Confecção").setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

function normalizarTexto(str) {
  return String(str || "")
    .normalize("NFD")
    .replace(/[̀-ͯ]/g, "")
    .replace(/[^\w\s]/g, "")
    .trim()
    .toLowerCase();
}

function validarLoginConfeccao(usuario, senha) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("senhas_atuais");
  const dados = aba.getDataRange().getValues();
  const userNorm = normalizarTexto(usuario);

  for (let i = 1; i < dados.length; i++) {
    const nomeOriginal = String(dados[i][0]).trim();
    const nomeNormalizado = normalizarTexto(nomeOriginal);
    const senhaEsperada = String(dados[i][2]).trim();

    if (userNorm === nomeNormalizado && senha === senhaEsperada) {
      return { ok: true, nomeOriginal: nomeOriginal };
    }
  }
  return { ok: false };
}


function getProdutosECoresValidos() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const produtos = new Set();
  const cores = new Set();

  for (let i = 1; i < dados.length; i++) {
    produtos.add(dados[i][4]); // Produto
    cores.add(dados[i][6]);    // Cor
  }

  return {
    produtos: Array.from(produtos).filter(Boolean),
    cores: Array.from(cores).filter(Boolean)
  };
}


function getConfecDisponiveis() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const dados = ss.getSheetByName("entrada_destinacao_tecido").getDataRange().getValues();
  const confs = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31]).trim();
    if (conf) confs.add(conf);
  }

  return Array.from(confs).sort();
}

// 🚀 Backend ajustado - getOPsComResumo


// Correção para garantir que o resumo seja enviado corretamente para o frontend


// ✅ BackendConfeccao.js - Revisado e pronto para deploy!

// 🌟 Backend revisado e garantido para carregar OPs
// getOPsComResumo corrigido para alinhar com o frontend
function getOPsComResumo(confec) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const resposta = [];

  let nomeOriginalConfec = null;

  Logger.log(`🧵 Buscando OPs para: ${confec}`);

  for (let i = 1; i < dados.length; i++) {
    const confLinha = String(dados[i][31] || "").trim(); // Nome da confecção
    if (confLinha === confec) {
      nomeOriginalConfec = confLinha;
      const op = String(dados[i][30] || "").trim();
      resposta.push({
        op: op,
        produto: dados[i][4] || "",
        cor: dados[i][6] || "",
        qtdEstimada: dados[i][18] || "-",
        qtdCortada: dados[i][19] || "-",
        dataEnvio: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "-"),
        dataFinalizacao: dados[i][39] || "-",
        statusCorte: [ // Alinhado com o frontend
          dados[i][35] || "⛔", // AJ
          dados[i][36] || "⛔", // AK
          dados[i][37] || "⛔", // AL
          dados[i][38] || "⛔", // AM
          dados[i][39] || "⛔"  // AN
        ].filter(Boolean).join(", ")
      });
    }
  }

  if (!nomeOriginalConfec) {
    Logger.log(`⚠️ Nenhuma OP encontrada para: ${confec}`);
    return { ok: false, nomeOriginal: confec, totalOPs: 0, listaOPs: [] };
  }

  Logger.log(`✅ ${resposta.length} OP(s) carregadas para ${nomeOriginalConfec}`);
  return { ok: true, nomeOriginal: nomeOriginalConfec, totalOPs: resposta.length, listaOPs: resposta };
}


function testarConfecDebug() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const encontrados = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31] || "").trim();
    if (conf) encontrados.add(conf);
  }

  Logger.log("🔍 Confecções únicas:", Array.from(encontrados));
  return Array.from(encontrados).sort();
}


// ✅ Testar Confecção Debug
function testarConfecDebug() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const encontrados = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31] || "").trim();
    if (conf) encontrados.add(conf);
  }

  Logger.log("🔍 Confecções únicas:", Array.from(encontrados));
  return Array.from(encontrados).sort();
}




function getDetalhesDaOP(op) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();

  const opAlvo = String(op || "").trim();
  Logger.log("🔍 OP recebida no frontend: " + opAlvo);

  for (let i = 1; i < dados.length; i++) {
    const opLinha = String(dados[i][30] || "").trim();

    if (opLinha === opAlvo) {
      Logger.log("✅ Match encontrado na linha " + (i + 1));
      return {
        produto: dados[i][4] || "-",
        cor: dados[i][6] || "-",
        tamanhos: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "Não informado"),
        confeccao: dados[i][31] || "-",
        qtdCortada: dados[i][18] && dados[i][18] > 0
        ? dados[i][18]
        : `Estimado: ${dados[i][19] || "N/A"}`,

        volumes: dados[i][20] || 0,
        dataEnvio: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "-"),
        status: [
          dados[i][35] || "⛔", // AJ
          dados[i][36] || "⛔", // AK
          dados[i][37] || "⛔", // AL
          dados[i][38] || "⛔", // AM
          dados[i][39] || "⛔"  // AN
        ].join(" / ")
      };
    }
  }

  Logger.log("❌ Nenhuma OP encontrada que bata com: " + opAlvo);
  return {
    erro: true,
    mensagem: `❌ OP "${op}" não encontrada.`,
    produto: "-", cor: "-", tamanhos: "-", confeccao: "-",
    qtdCortada: 0, volumes: 0, dataEnvio: "-", status: "Não encontrado"
  };
}


function registrarRetornoManual(payload) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const abaTecido = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = abaTecido.getDataRange().getValues();

  const {
    produto, cor, tamanhos, qtdTotal, confec, dataInicio, dataFim,
    responsavel, custoUnitario, observacoes
  } = payload;

  let opAssociada = "";
  for (let i = 1; i < dados.length; i++) {
    const confLinha = normalizarTexto(dados[i][31]);
    const prodLinha = normalizarTexto(dados[i][4]);
    const corLinha = normalizarTexto(dados[i][6]);
    const op = dados[i][30];
    const estimada = parseInt(dados[i][18]) || 0;

    if (confLinha === normalizarTexto(confec) && prodLinha === normalizarTexto(produto) && corLinha === normalizarTexto(cor)) {
      const margem = Math.abs(estimada - qtdTotal) / estimada;
      if (margem <= 0.1) {
        opAssociada = op;
        break;
      }
    }
  }

  abaLog.appendRow([
    new Date(),
    opAssociada || "N/A",
    produto,
    cor,
    tamanhos,
    confec,
    dataInicio,
    dataFim,
    qtdTotal,
    custoUnitario,
    observacoes,
    responsavel,
    "manual"
  ]);

  return `✅ Retorno manual registrado. ${opAssociada ? "OP associada: " + opAssociada : "Sem OP associada."}`;
}

function registrarRetornoConfeccao(payload) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();

  const opNormalizada = normalizarTexto(payload.op);

  let linhaEntrada = -1;
  let produto = "";
  let cor = "";
  let confec = "";
  let dataPrevista = "";

  for (let i = 1; i < dadosEntrada.length; i++) {
    const opLinha = normalizarTexto(dadosEntrada[i][30]);
    if (opLinha === opNormalizada) {
      linhaEntrada = i + 1;
      produto = dadosEntrada[i][4];
      cor = dadosEntrada[i][6];
      confec = dadosEntrada[i][31];
      dataPrevista = dadosEntrada[i][37];
      break;
    }
  }

  if (linhaEntrada === -1) throw new Error("❌ OP não encontrada na aba entrada_destinacao_tecido.");

  // Log completo
  abaLog.appendRow([
    confec,
    new Date(),
    payload.op,
    produto,
    cor,
    dataPrevista || "",
    "", "", "", "", "", "", "", "", "", "", "", "", "", "",
    payload.qtdP,
    payload.qtdM,
    payload.qtdG,
    payload.qtdGG,
    payload.qtdXG,
    payload.total,
    payload.retorno,
    "", "", "", payload.vencimento,
    "", "", "", "", "", "",
    payload.conforme === "Sim" ? "Entregue na confecção" : `Não conforme: ${payload.motivos.join(", ")}`,
    "Costura finalizada"
  ]);

  // Correto para os campos AL e AM
  abaEntrada.getRange(linhaEntrada, 38).setValue("Recebido na Confecção"); // AL
  abaEntrada.getRange(linhaEntrada, 39).setValue("Costura finalizada");    // AM

  return `✅ Retorno registrado com sucesso para OP ${payload.op}.`;
}




function gerarPDFRomaneio(opSelecionada, motivoSegundaQualidade) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("log_confeccao");
  const dados = aba.getDataRange().getValues();

  const headers = dados[0];
  const idxOP = headers.indexOf("OP");
  const linha = dados.find(row => String(row[idxOP]).trim() === String(opSelecionada).trim());

  if (!linha) throw new Error("❌ OP não encontrada no log_confeccao.");

  const [
    confec, dataRegistro, op, produto, cor, dataPrevista,
    , , , , , , , , , , , , , , // Pula campos irrelevantes até U
    qtdP, qtdM, qtdG, qtdGG, qtdXG,
    totalCosturado, dataFinal, , , , vencimento,
    , , , , , ,
    statusRecebimento, statusAtual
  ] = linha;

  const html = `
    <html>
    <head>
      <style>
        body { font-family: Arial, sans-serif; padding: 40px; }
        h1 { text-align: center; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        td, th { border: 1px solid #ccc; padding: 8px; text-align: left; }
        .info { margin-top: 20px; }
        .info strong { display: inline-block; width: 200px; }
      </style>
    </head>
    <body>
      <h1>🧵 Romaneio de Retorno - Costura</h1>
      <div class="info">
        <p><strong>OP:</strong> ${op}</p>
        <p><strong>Produto:</strong> ${produto}</p>
        <p><strong>Cor:</strong> ${cor}</p>
        <p><strong>Confecção:</strong> ${confec}</p>
        <p><strong>Data Registro:</strong> ${new Date(dataRegistro).toLocaleDateString("pt-BR")}</p>
        <p><strong>Status Atual:</strong> ${statusAtual}</p>
        <p><strong>Recebimento:</strong> ${statusRecebimento}</p>
      </div>

      <table>
        <thead>
          <tr>
            <th>Tamanho</th>
            <th>Qtd</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>P</td><td>${qtdP || 0}</td></tr>
          <tr><td>M</td><td>${qtdM || 0}</td></tr>
          <tr><td>G</td><td>${qtdG || 0}</td></tr>
          <tr><td>GG</td><td>${qtdGG || 0}</td></tr>
          <tr><td>XG</td><td>${qtdXG || 0}</td></tr>
        </tbody>
        <tfoot>
          <tr><th>Total</th><th>${totalCosturado || 0}</th></tr>
        </tfoot>
      </table>

      <div class="info">
        <p><strong>Data de Finalização:</strong> ${dataFinal}</p>
        <p><strong>Data de Vencimento:</strong> ${vencimento || "-"}</p>
        <p><strong>Peças Segunda Qualidade:</strong><br>${motivoSegundaQualidade || "-"}</p>
      </div>

      <div style="margin-top:40px; text-align: center;">
        <em>Gerado via sistema Orbitta x Berzerk</em>
      </div>
    </body>
    </html>
  `;

  const blob = Utilities.newBlob(html, "text/html", `Romaneio_OP_${op}.html`);
  const url = DriveApp.createFile(blob).getDownloadUrl();
  return url;
}

function atualizarStatusOPConfec(op, novoStatus, precisaConformidade) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();

  const normalizar = s => String(s || "")
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "")
    .replace(/[^\w\s]/g, "")
    .toLowerCase()
    .trim();

  const opNormalizada = String(op || "").trim().toLowerCase();

  for (let i = 1; i < dados.length; i++) {
    const opLinha = normalizar(dados[i][30]);
    if (opLinha === opNormalizada) {
      aba.getRange(i + 1, 38).setValue(novoStatus); // AM
      if (precisaConformidade) {
        aba.getRange(i + 1, 37).setValue("Entregue na confecção"); // AL
      }
      Logger.log(`✅ Status da OP ${op} atualizado para ${novoStatus}`);
      return `Status atualizado para "${novoStatus}"`;
    }
  }

  throw new Error(`❌ OP "${op}" não encontrada para atualizar status.`);
}




// Função para baixar o CSV com os registros da confecção
function baixarCSVConfec() {
  google.script.run.withSuccessHandler(function(url) {
    if (url) {
      window.open(url, '_blank');
    } else {
      alert("❌ Erro ao gerar o CSV. Verifique se há registros para baixar.");
    }
  }).gerarCSVConfec(usuarioLogado);
}

// Função para gerar Romaneio (PDF) da OP selecionada
function gerarRomaneioPDF() {
  if (!opSelecionada) {
    alert("Selecione uma OP antes de gerar o Romaneio.");
    return;
  }

  google.script.run.withSuccessHandler(function(url) {
    if (url) {
      window.open(url, '_blank');
    } else {
      alert("❌ Erro ao gerar o PDF. Tente novamente.");
    }
  }).gerarPDFRomaneio(opSelecionada);
}

// ✅ Adiciona início de costura no log_confeccao

// ✅ Funções backend para registrar ações com fallback de criação de OP no log_confeccao

// ✅ Funções backend para registrar ações com fallback de criação de OP no log_confeccao

function registrarRecebimentoCondicional(op, conforme, motivo) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date(); // Data de Acesso
    novaLinha[2] = linhaEntrada[30]; // OP
    novaLinha[3] = linhaEntrada[4]; // Produto
    novaLinha[4] = linhaEntrada[6]; // Cor
    novaLinha[5] = linhaEntrada[7]; // Data Prevista
    novaLinha[6] = linhaEntrada[8]; // PCs Estimadas
    novaLinha[18] = new Date(); // Data Real Entrega Confecção (coluna S)
    novaLinha[21] = conforme ? "Recebido na confecção" : `Recebimento com problema: ${motivo}`; // Status (coluna V)
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 19).setValue(new Date()); // Coluna S
    abaLog.getRange(linha + 1, 22).setValue(conforme ? "Recebido na confecção" : `Recebimento com problema: ${motivo}`); // Coluna V
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 38).setValue("Recebido na Confecção"); // Coluna AL
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}

function registrarInicioCondicional(op) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date();
    novaLinha[2] = linhaEntrada[30];
    novaLinha[3] = linhaEntrada[4];
    novaLinha[4] = linhaEntrada[6];
    novaLinha[5] = linhaEntrada[7];
    novaLinha[6] = linhaEntrada[8];
    novaLinha[20] = new Date(); // Coluna U
    novaLinha[21] = "Costura em andamento"; // Coluna V
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 21).setValue(new Date()); // Coluna U
    abaLog.getRange(linha + 1, 22).setValue("Costura em andamento"); // Coluna V
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}

function registrarConclusaoCondicional(op, defeitos, classificacao, dataRetirada, foiConforme) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date();
    novaLinha[2] = linhaEntrada[30];
    novaLinha[3] = linhaEntrada[4];
    novaLinha[4] = linhaEntrada[6];
    novaLinha[5] = linhaEntrada[7];
    novaLinha[6] = linhaEntrada[8];
    novaLinha[27] = new Date(); // Coluna AB
    novaLinha[28] = dataRetirada; // Coluna AC
    novaLinha[21] = foiConforme ? "Costura finalizada conforme" : `Finalização com defeitos: ${defeitos} (${classificacao})`; // Coluna V
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 28).setValue(new Date()); // Coluna AB
    abaLog.getRange(linha + 1, 29).setValue(dataRetirada); // Coluna AC
    abaLog.getRange(linha + 1, 22).setValue(
      foiConforme ? "Costura finalizada conforme" : `Finalização com defeitos: ${defeitos} (${classificacao})`
    );
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 39).setValue("Costura finalizada"); // Coluna AM
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}

<!-- painelConfeccao.html - VERSÃO COMPLETA E FUNCIONAL -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>✅ Painel Confecção</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Poppins', sans-serif; background-color: #f1f5f9; padding: 1rem; }
    h1 { font-size: 1.5rem; margin-bottom: 1rem; text-align: center; }
    .resumo-box { background-color: #fff; border: 1px solid #ccc; padding: 1rem; border-radius: 0.5rem; margin-top: 1rem; }
  </style>
</head>
<body>
  <div id="loginBox">
    <h1>🔐 Acesso Confecção</h1>
    <div class="mb-4">
      <input id="usuario" placeholder="Confecção" class="border rounded p-2 w-full" />
    </div>
    <div class="mb-4">
      <input id="senha" type="password" placeholder="Senha" class="border rounded p-2 w-full" />
    </div>
    <button onclick="fazerLogin()" class="bg-blue-600 text-white px-4 py-2 rounded">Entrar</button>
  </div>

  <div id="painelConf" style="display:none">
    <h1>Confecção: <span id="nomeConfec"></span></h1>
    <div id="listaOps" class="overflow-x-auto mt-4"></div>
    <div id="blocoResumo" class="resumo-box" style="display:none"></div>
    <div id="formularioRetorno" class="mt-4" style="display:none"></div>
    <div id="confirmacaoBox" class="mt-4" style="display:none">
      <button onclick="confirmarAcao()" class="bg-green-600 text-white px-4 py-2 rounded">✅ Confirmar Ação</button>
    </div>
  </div>

  <script>
    let usuarioLogado = "";
    let opSelecionada = "";
    let acaoPendente = null;
    let dadosAcao = {};

    function fazerLogin() {
      const u = document.getElementById("usuario").value;
      const s = document.getElementById("senha").value;
      google.script.run.withSuccessHandler(function(resp) {
        if (resp.ok) {
          usuarioLogado = resp.nomeOriginal;
          document.getElementById("loginBox").style.display = "none";
          document.getElementById("painelConf").style.display = "block";
          document.getElementById("nomeConfec").innerText = usuarioLogado;
          carregarOPsDisponiveis();
        } else {
          alert("❌ Login inválido!");
        }
      }).validarLoginConfeccao(u, s);
    }

    function carregarOPsDisponiveis() {
      google.script.run.withSuccessHandler(function(res) {
        if (!res.ok || res.listaOPs.length === 0) {
          document.getElementById("listaOps").innerHTML = "<p>Nenhuma OP encontrada.</p>";
          return;
        }
        let html = `<table class='min-w-full border'><thead><tr class='bg-gray-200'>
          <th class='border px-2'>OP</th><th class='border px-2'>Produto</th><th class='border px-2'>Cor</th>
          <th class='border px-2'>Qtd Cortada</th><th class='border px-2'>Status</th><th class='border px-2'>Ação</th>
        </tr></thead><tbody>`;
        res.listaOPs.forEach(op => {
          html += `<tr>
            <td class='border px-2'>${op.op}</td>
            <td class='border px-2'>${op.produto}</td>
            <td class='border px-2'>${op.cor}</td>
            <td class='border px-2'>${op.qtdCortada}</td>
            <td class='border px-2'>${op.statusCorte}</td>
            <td class='border px-2'>
              <button onclick="selecionarOP('${op.op}')" class='bg-yellow-400 px-2 py-1 rounded'>Selecionar</button>
            </td>
          </tr>`;
        });
        html += `</tbody></table>`;
        document.getElementById("listaOps").innerHTML = html;
      }).getOPsComResumo(usuarioLogado);
    }

    function selecionarOP(op) {
      opSelecionada = op;
      google.script.run.withSuccessHandler(function(resumo) {
        if (!resumo || !resumo.produto) {
          alert("❌ OP não encontrada.");
          return;
        }
        let html = `<h2 class='font-bold text-lg mb-2'>Resumo da OP ${op}</h2>`;
        html += `<p><strong>Produto:</strong> ${resumo.produto}</p>`;
        html += `<p><strong>Cor:</strong> ${resumo.cor}</p>`;
        html += `<p><strong>Confecção:</strong> ${resumo.confec}</p>`;
        html += `<p><strong>Status atual:</strong> ${resumo.status}</p>`;
        html += `<p><strong>Qtd Cortada:</strong> ${resumo.qtdCortada}</p>`;
        html += `<p><strong>Qtd Estimada:</strong> ${resumo.qtdEstimada}</p>`;
        html += `<p><strong>Data Finalização:</strong> ${resumo.dataFinalizacao}</p>`;
        html += `<div class='mt-4'>
          <label class='block'>🔧 Ação:</label>
          <select class='border rounded p-2 w-full' onchange="prepararAcao(this.value)">
            <option value="">-- Selecione --</option>
            <option value="receber">Receber na confecção</option>
            <option value="iniciar">Iniciar costura</option>
            <option value="finalizar">Finalizar costura</option>
          </select>
        </div>`;
        document.getElementById("blocoResumo").style.display = "block";
        document.getElementById("blocoResumo").innerHTML = html;
      }).getDetalhesDaOP(op);
    }

    function prepararAcao(tipo) {
      if (!opSelecionada) return;
      acaoPendente = tipo;
      dadosAcao = {};
      let html = "";

      if (tipo === "receber") {
        html += `<label class='block mt-2'>Conforme?
          <select id='conforme' class='border rounded p-2 w-full'>
            <option value='Sim'>Sim</option>
            <option value='Não'>Não</option>
          </select>
        </label>
        <label class='block mt-2'>Motivo (se não conforme):
          <input id='motivo' class='border rounded p-2 w-full' placeholder='Descreva o problema' />
        </label>`;
      } else if (tipo === "finalizar") {
        html += `<div class='grid grid-cols-2 gap-2 mt-2'>`;
        ['P','M','G','GG','XG'].forEach(t => {
          html += `<label>${t}<input type='number' id='qtd${t}' class='border rounded p-2 w-full' value='0'></label>`;
        });
        html += `</div>
        <label class='block mt-2'>Conforme?
          <select id='foiConforme' class='border rounded p-2 w-full'>
            <option value='Sim'>Sim</option>
            <option value='Não'>Não</option>
          </select>
        </label>
        <label class='block mt-2'>Defeitos (se não conforme):
          <input id='defeitos' class='border rounded p-2 w-full' placeholder='Descreva defeitos' />
        </label>
        <label class='block mt-2'>Classificação:
          <input id='classificacao' class='border rounded p-2 w-full' placeholder='Grave, leve, etc' />
        </label>
        <label class='block mt-2'>Data Retirada:
          <input id='dataRetirada' class='border rounded p-2 w-full' type='date' />
        </label>`;
      }

      document.getElementById("formularioRetorno").innerHTML = html;
      document.getElementById("formularioRetorno").style.display = "block";
      document.getElementById("confirmacaoBox").style.display = "block";
    }

    function confirmarAcao() {
      if (!acaoPendente || !opSelecionada) return;

      if (acaoPendente === "receber") {
        const conforme = document.getElementById('conforme').value;
        const motivo = document.getElementById('motivo').value;
        google.script.run.registrarRecebimentoCondicional(opSelecionada, conforme === 'Sim', motivo);

      } else if (acaoPendente === "iniciar") {
        google.script.run.registrarInicioCondicional(opSelecionada);

      } else if (acaoPendente === "finalizar") {
        const payload = {
          qtdP: parseInt(document.getElementById('qtdP').value || 0),
          qtdM: parseInt(document.getElementById('qtdM').value || 0),
          qtdG: parseInt(document.getElementById('qtdG').value || 0),
          qtdGG: parseInt(document.getElementById('qtdGG').value || 0),
          qtdXG: parseInt(document.getElementById('qtdXG').value || 0),
          defeitos: document.getElementById('defeitos').value,
          classificacao: document.getElementById('classificacao').value,
          dataRetirada: document.getElementById('dataRetirada').value,
          foiConforme: document.getElementById('foiConforme').value === 'Sim'
        };
        google.script.run.registrarConclusaoCondicional(
          opSelecionada,
          payload.defeitos,
          payload.classificacao,
          payload.dataRetirada,
          payload.foiConforme
        );
        setTimeout(() => {
          if (confirm("Deseja gerar o PDF de Romaneio agora?")) {
            google.script.run.withSuccessHandler(function(url) {
              window.open(url, '_blank');
            }).gerarPDFRomaneio(opSelecionada);
          }
        }, 500);
      }

      alert("✅ Ação registrada com sucesso.");
      document.getElementById("confirmacaoBox").style.display = "none";
      document.getElementById("formularioRetorno").style.display = "none";
      carregarOPsDisponiveis();
    }
  </script>
</body>
</html>

// ✅ Correção definitiva backendConfeccao.gs com suporte a nomes com acento

function doGet(e) {
  const template = HtmlService.createTemplateFromFile("painelConfeccao");
  return template.evaluate().setTitle("Painel Confecção").setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

function normalizarTexto(str) {
  return String(str || "")
    .normalize("NFD")
    .replace(/[̀-ͯ]/g, "")
    .replace(/[^\w\s]/g, "")
    .trim()
    .toLowerCase();
}

function validarLoginConfeccao(usuario, senha) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("senhas_atuais");
  const dados = aba.getDataRange().getValues();
  const userNorm = normalizarTexto(usuario);

  for (let i = 1; i < dados.length; i++) {
    const nomeOriginal = String(dados[i][0]).trim();
    const nomeNormalizado = normalizarTexto(nomeOriginal);
    const senhaEsperada = String(dados[i][2]).trim();

    if (userNorm === nomeNormalizado && senha === senhaEsperada) {
      return { ok: true, nomeOriginal: nomeOriginal };
    }
  }
  return { ok: false };
}


function getProdutosECoresValidos() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const produtos = new Set();
  const cores = new Set();

  for (let i = 1; i < dados.length; i++) {
    produtos.add(dados[i][4]); // Produto
    cores.add(dados[i][6]);    // Cor
  }

  return {
    produtos: Array.from(produtos).filter(Boolean),
    cores: Array.from(cores).filter(Boolean)
  };
}


function getConfecDisponiveis() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const dados = ss.getSheetByName("entrada_destinacao_tecido").getDataRange().getValues();
  const confs = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31]).trim();
    if (conf) confs.add(conf);
  }

  return Array.from(confs).sort();
}

// 🚀 Backend ajustado - getOPsComResumo


// Correção para garantir que o resumo seja enviado corretamente para o frontend


// ✅ BackendConfeccao.js - Revisado e pronto para deploy!

// 🌟 Backend revisado e garantido para carregar OPs
// getOPsComResumo corrigido para alinhar com o frontend
function getOPsComResumo(confec) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const resposta = [];

  let nomeOriginalConfec = null;

  Logger.log(`🧵 Buscando OPs para: ${confec}`);

  for (let i = 1; i < dados.length; i++) {
    const confLinha = String(dados[i][31] || "").trim(); // Nome da confecção
    if (confLinha === confec) {
      nomeOriginalConfec = confLinha;
      const op = String(dados[i][30] || "").trim();
      resposta.push({
        op: op,
        produto: dados[i][4] || "",
        cor: dados[i][6] || "",
        qtdEstimada: dados[i][18] || "-",
        qtdCortada: dados[i][19] || "-",
        dataEnvio: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "-"),
        dataFinalizacao: dados[i][39] || "-",
        statusCorte: [ // Alinhado com o frontend
          dados[i][35] || "⛔", // AJ
          dados[i][36] || "⛔", // AK
          dados[i][37] || "⛔", // AL
          dados[i][38] || "⛔", // AM
          dados[i][39] || "⛔"  // AN
        ].filter(Boolean).join(", ")
      });
    }
  }

  if (!nomeOriginalConfec) {
    Logger.log(`⚠️ Nenhuma OP encontrada para: ${confec}`);
    return { ok: false, nomeOriginal: confec, totalOPs: 0, listaOPs: [] };
  }

  Logger.log(`✅ ${resposta.length} OP(s) carregadas para ${nomeOriginalConfec}`);
  return { ok: true, nomeOriginal: nomeOriginalConfec, totalOPs: resposta.length, listaOPs: resposta };
}


function testarConfecDebug() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const encontrados = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31] || "").trim();
    if (conf) encontrados.add(conf);
  }

  Logger.log("🔍 Confecções únicas:", Array.from(encontrados));
  return Array.from(encontrados).sort();
}


// ✅ Testar Confecção Debug
function testarConfecDebug() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();
  const encontrados = new Set();

  for (let i = 1; i < dados.length; i++) {
    const conf = String(dados[i][31] || "").trim();
    if (conf) encontrados.add(conf);
  }

  Logger.log("🔍 Confecções únicas:", Array.from(encontrados));
  return Array.from(encontrados).sort();
}




function getDetalhesDaOP(op) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();

  const opAlvo = String(op || "").trim();
  Logger.log("🔍 OP recebida no frontend: " + opAlvo);

  for (let i = 1; i < dados.length; i++) {
    const opLinha = String(dados[i][30] || "").trim();

    if (opLinha === opAlvo) {
      Logger.log("✅ Match encontrado na linha " + (i + 1));
      return {
        produto: dados[i][4] || "-",
        cor: dados[i][6] || "-",
        tamanhos: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "Não informado"),
        confeccao: dados[i][31] || "-",
        qtdCortada: dados[i][18] && dados[i][18] > 0
        ? dados[i][18]
        : `Estimado: ${dados[i][19] || "N/A"}`,

        volumes: dados[i][20] || 0,
        dataEnvio: dados[i][9] instanceof Date
          ? Utilities.formatDate(dados[i][9], Session.getScriptTimeZone(), "dd/MM/yyyy")
          : (dados[i][9] || "-"),
        status: [
          dados[i][35] || "⛔", // AJ
          dados[i][36] || "⛔", // AK
          dados[i][37] || "⛔", // AL
          dados[i][38] || "⛔", // AM
          dados[i][39] || "⛔"  // AN
        ].join(" / ")
      };
    }
  }

  Logger.log("❌ Nenhuma OP encontrada que bata com: " + opAlvo);
  return {
    erro: true,
    mensagem: `❌ OP "${op}" não encontrada.`,
    produto: "-", cor: "-", tamanhos: "-", confeccao: "-",
    qtdCortada: 0, volumes: 0, dataEnvio: "-", status: "Não encontrado"
  };
}


function registrarRetornoManual(payload) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const abaTecido = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = abaTecido.getDataRange().getValues();

  const {
    produto, cor, tamanhos, qtdTotal, confec, dataInicio, dataFim,
    responsavel, custoUnitario, observacoes
  } = payload;

  let opAssociada = "";
  for (let i = 1; i < dados.length; i++) {
    const confLinha = normalizarTexto(dados[i][31]);
    const prodLinha = normalizarTexto(dados[i][4]);
    const corLinha = normalizarTexto(dados[i][6]);
    const op = dados[i][30];
    const estimada = parseInt(dados[i][18]) || 0;

    if (confLinha === normalizarTexto(confec) && prodLinha === normalizarTexto(produto) && corLinha === normalizarTexto(cor)) {
      const margem = Math.abs(estimada - qtdTotal) / estimada;
      if (margem <= 0.1) {
        opAssociada = op;
        break;
      }
    }
  }

  abaLog.appendRow([
    new Date(),
    opAssociada || "N/A",
    produto,
    cor,
    tamanhos,
    confec,
    dataInicio,
    dataFim,
    qtdTotal,
    custoUnitario,
    observacoes,
    responsavel,
    "manual"
  ]);

  return `✅ Retorno manual registrado. ${opAssociada ? "OP associada: " + opAssociada : "Sem OP associada."}`;
}

function registrarRetornoConfeccao(payload) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();

  const opNormalizada = normalizarTexto(payload.op);

  let linhaEntrada = -1;
  let produto = "";
  let cor = "";
  let confec = "";
  let dataPrevista = "";

  for (let i = 1; i < dadosEntrada.length; i++) {
    const opLinha = normalizarTexto(dadosEntrada[i][30]);
    if (opLinha === opNormalizada) {
      linhaEntrada = i + 1;
      produto = dadosEntrada[i][4];
      cor = dadosEntrada[i][6];
      confec = dadosEntrada[i][31];
      dataPrevista = dadosEntrada[i][37];
      break;
    }
  }

  if (linhaEntrada === -1) throw new Error("❌ OP não encontrada na aba entrada_destinacao_tecido.");

  // Log completo
  abaLog.appendRow([
    confec,
    new Date(),
    payload.op,
    produto,
    cor,
    dataPrevista || "",
    "", "", "", "", "", "", "", "", "", "", "", "", "", "",
    payload.qtdP,
    payload.qtdM,
    payload.qtdG,
    payload.qtdGG,
    payload.qtdXG,
    payload.total,
    payload.retorno,
    "", "", "", payload.vencimento,
    "", "", "", "", "", "",
    payload.conforme === "Sim" ? "Entregue na confecção" : `Não conforme: ${payload.motivos.join(", ")}`,
    "Costura finalizada"
  ]);

  // Correto para os campos AL e AM
  abaEntrada.getRange(linhaEntrada, 38).setValue("Recebido na Confecção"); // AL
  abaEntrada.getRange(linhaEntrada, 39).setValue("Costura finalizada");    // AM

  return `✅ Retorno registrado com sucesso para OP ${payload.op}.`;
}




function gerarPDFRomaneio(opSelecionada, motivoSegundaQualidade) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("log_confeccao");
  const dados = aba.getDataRange().getValues();

  const headers = dados[0];
  const idxOP = headers.indexOf("OP");
  const linha = dados.find(row => String(row[idxOP]).trim() === String(opSelecionada).trim());

  if (!linha) throw new Error("❌ OP não encontrada no log_confeccao.");

  const [
    confec, dataRegistro, op, produto, cor, dataPrevista,
    , , , , , , , , , , , , , , // Pula campos irrelevantes até U
    qtdP, qtdM, qtdG, qtdGG, qtdXG,
    totalCosturado, dataFinal, , , , vencimento,
    , , , , , ,
    statusRecebimento, statusAtual
  ] = linha;

  const html = `
    <html>
    <head>
      <style>
        body { font-family: Arial, sans-serif; padding: 40px; }
        h1 { text-align: center; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        td, th { border: 1px solid #ccc; padding: 8px; text-align: left; }
        .info { margin-top: 20px; }
        .info strong { display: inline-block; width: 200px; }
      </style>
    </head>
    <body>
      <h1>🧵 Romaneio de Retorno - Costura</h1>
      <div class="info">
        <p><strong>OP:</strong> ${op}</p>
        <p><strong>Produto:</strong> ${produto}</p>
        <p><strong>Cor:</strong> ${cor}</p>
        <p><strong>Confecção:</strong> ${confec}</p>
        <p><strong>Data Registro:</strong> ${new Date(dataRegistro).toLocaleDateString("pt-BR")}</p>
        <p><strong>Status Atual:</strong> ${statusAtual}</p>
        <p><strong>Recebimento:</strong> ${statusRecebimento}</p>
      </div>

      <table>
        <thead>
          <tr>
            <th>Tamanho</th>
            <th>Qtd</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>P</td><td>${qtdP || 0}</td></tr>
          <tr><td>M</td><td>${qtdM || 0}</td></tr>
          <tr><td>G</td><td>${qtdG || 0}</td></tr>
          <tr><td>GG</td><td>${qtdGG || 0}</td></tr>
          <tr><td>XG</td><td>${qtdXG || 0}</td></tr>
        </tbody>
        <tfoot>
          <tr><th>Total</th><th>${totalCosturado || 0}</th></tr>
        </tfoot>
      </table>

      <div class="info">
        <p><strong>Data de Finalização:</strong> ${dataFinal}</p>
        <p><strong>Data de Vencimento:</strong> ${vencimento || "-"}</p>
        <p><strong>Peças Segunda Qualidade:</strong><br>${motivoSegundaQualidade || "-"}</p>
      </div>

      <div style="margin-top:40px; text-align: center;">
        <em>Gerado via sistema Orbitta x Berzerk</em>
      </div>
    </body>
    </html>
  `;

  const blob = Utilities.newBlob(html, "text/html", `Romaneio_OP_${op}.html`);
  const url = DriveApp.createFile(blob).getDownloadUrl();
  return url;
}

function atualizarStatusOPConfec(op, novoStatus, precisaConformidade) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("entrada_destinacao_tecido");
  const dados = aba.getDataRange().getValues();

  const normalizar = s => String(s || "")
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "")
    .replace(/[^\w\s]/g, "")
    .toLowerCase()
    .trim();

  const opNormalizada = String(op || "").trim().toLowerCase();

  for (let i = 1; i < dados.length; i++) {
    const opLinha = normalizar(dados[i][30]);
    if (opLinha === opNormalizada) {
      aba.getRange(i + 1, 38).setValue(novoStatus); // AM
      if (precisaConformidade) {
        aba.getRange(i + 1, 37).setValue("Entregue na confecção"); // AL
      }
      Logger.log(`✅ Status da OP ${op} atualizado para ${novoStatus}`);
      return `Status atualizado para "${novoStatus}"`;
    }
  }

  throw new Error(`❌ OP "${op}" não encontrada para atualizar status.`);
}




// Função para baixar o CSV com os registros da confecção
function baixarCSVConfec() {
  google.script.run.withSuccessHandler(function(url) {
    if (url) {
      window.open(url, '_blank');
    } else {
      alert("❌ Erro ao gerar o CSV. Verifique se há registros para baixar.");
    }
  }).gerarCSVConfec(usuarioLogado);
}

// Função para gerar Romaneio (PDF) da OP selecionada
function gerarRomaneioPDF() {
  if (!opSelecionada) {
    alert("Selecione uma OP antes de gerar o Romaneio.");
    return;
  }

  google.script.run.withSuccessHandler(function(url) {
    if (url) {
      window.open(url, '_blank');
    } else {
      alert("❌ Erro ao gerar o PDF. Tente novamente.");
    }
  }).gerarPDFRomaneio(opSelecionada);
}

// ✅ Adiciona início de costura no log_confeccao

// ✅ Funções backend para registrar ações com fallback de criação de OP no log_confeccao

// ✅ Funções backend para registrar ações com fallback de criação de OP no log_confeccao

function registrarRecebimentoCondicional(op, conforme, motivo) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date(); // Data de Acesso
    novaLinha[2] = linhaEntrada[30]; // OP
    novaLinha[3] = linhaEntrada[4]; // Produto
    novaLinha[4] = linhaEntrada[6]; // Cor
    novaLinha[5] = linhaEntrada[7]; // Data Prevista
    novaLinha[6] = linhaEntrada[8]; // PCs Estimadas
    novaLinha[18] = new Date(); // Data Real Entrega Confecção (coluna S)
    novaLinha[21] = conforme ? "Recebido na confecção" : `Recebimento com problema: ${motivo}`; // Status (coluna V)
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 19).setValue(new Date()); // Coluna S
    abaLog.getRange(linha + 1, 22).setValue(conforme ? "Recebido na confecção" : `Recebimento com problema: ${motivo}`); // Coluna V
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 38).setValue("Recebido na Confecção"); // Coluna AL
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}

function registrarInicioCondicional(op) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date();
    novaLinha[2] = linhaEntrada[30];
    novaLinha[3] = linhaEntrada[4];
    novaLinha[4] = linhaEntrada[6];
    novaLinha[5] = linhaEntrada[7];
    novaLinha[6] = linhaEntrada[8];
    novaLinha[20] = new Date(); // Coluna U
    novaLinha[21] = "Costura em andamento"; // Coluna V
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 21).setValue(new Date()); // Coluna U
    abaLog.getRange(linha + 1, 22).setValue("Costura em andamento"); // Coluna V
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}

function registrarConclusaoCondicional(op, defeitos, classificacao, dataRetirada, foiConforme) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_confeccao");
  const dadosLog = abaLog.getDataRange().getValues();
  let linha = dadosLog.findIndex(r => String(r[2]).trim() === op);

  const abaEntrada = ss.getSheetByName("entrada_destinacao_tecido");
  const dadosEntrada = abaEntrada.getDataRange().getValues();
  const linhaEntradaIndex = dadosEntrada.findIndex(r => String(r[30]).trim() === op);
  const linhaEntrada = dadosEntrada[linhaEntradaIndex];

  if (linha === -1 && linhaEntrada) {
    const novaLinha = Array(38).fill("");
    novaLinha[0] = linhaEntrada[31]; // Confecção
    novaLinha[1] = new Date();
    novaLinha[2] = linhaEntrada[30];
    novaLinha[3] = linhaEntrada[4];
    novaLinha[4] = linhaEntrada[6];
    novaLinha[5] = linhaEntrada[7];
    novaLinha[6] = linhaEntrada[8];
    novaLinha[27] = new Date(); // Coluna AB
    novaLinha[28] = dataRetirada; // Coluna AC
    novaLinha[21] = foiConforme ? "Costura finalizada conforme" : `Finalização com defeitos: ${defeitos} (${classificacao})`; // Coluna V
    abaLog.appendRow(novaLinha);
  } else if (linha !== -1) {
    abaLog.getRange(linha + 1, 28).setValue(new Date()); // Coluna AB
    abaLog.getRange(linha + 1, 29).setValue(dataRetirada); // Coluna AC
    abaLog.getRange(linha + 1, 22).setValue(
      foiConforme ? "Costura finalizada conforme" : `Finalização com defeitos: ${defeitos} (${classificacao})`
    );
  }

  if (linhaEntradaIndex > -1) {
    abaEntrada.getRange(linhaEntradaIndex + 1, 39).setValue("Costura finalizada"); // Coluna AM
    abaEntrada.getRange(linhaEntradaIndex + 1, 30).setValue("✔️" + op);
  }
}


a confecçõ quando recebe> deve preencher um checklist de conformidade no recebimento, afirmando se recebeu e conferiu os volumes entreguese depois que elas finalizam a costura e agendam a retirada com a logística, deve ser avisado e o estoque deve receber pra também confirmar se veio costurado certo, se recebemos os pacotes certo


<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>📦 Painel de Estoque - Berzerk</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet" />
  <style>
    body { font-family: 'Poppins', sans-serif; }
    #toastSucesso {
      position: fixed;
      top: 20px;
      right: 20px;
      background-color: #38a169;
      color: white;
      padding: 12px 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
      display: none;
      z-index: 9999;
    }
  </style>
</head>
<body class="bg-gray-100 text-sm p-6">
  <div class="max-w-5xl mx-auto bg-white rounded-xl shadow p-6 space-y-6">
    <h1 class="text-2xl font-bold">📦 Painel de Estoque - Berzerk</h1>

    <div id="toastSucesso">✅ Movimentacao registrada com sucesso!</div>
    <div id="toastCarregando" style="display: none; position: fixed; top: 70px; right: 20px; background-color: #3182ce; color: white; padding: 12px 20px; border-radius: 8px; box-shadow: 0 2px 6px rgba(0,0,0,0.2); z-index: 9999;">
      ⏳ Registrando movimentacao...
    </div>

    <a href="https://script.google.com/a/macros/berzerk.com.br/s/AKfycbzyUTD1-_FnIGx6ERicjjULDiHHDUhhGnH9SB7bSCA86fQDlhz_zk5_rsWjUZFHgbjgaA/exec?painel=dashEstoque" target="_blank" class="inline-block bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
      📊 Acessar Dash de Estoque
    </a>

    <div id="selecaoTipoMovimentacao">
      <h2 class="text-xl font-semibold mb-4">Selecione o tipo de movimentação:</h2>
      <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
        <button onclick="selecionarTipo('Entrada - Pulmão')" class="card-tipo bg-blue-100 hover:bg-blue-200">
          <h3 class="font-bold text-blue-700">Recebimento de Produção</h3>
          <p class="text-sm text-gray-700">Entra no estoque Pulmão.</p>
        </button>
        <button onclick="selecionarTipo('Entrada - Direto para Estampar')" class="card-tipo bg-green-100 hover:bg-green-200">
          <h3 class="font-bold text-green-700">Entrada Direta na Estamparia</h3>
          <p class="text-sm text-gray-700">Já entra como produto estampado.</p>
        </button>
        <button onclick="selecionarTipo('Saída - Estampar')" class="card-tipo bg-yellow-100 hover:bg-yellow-200">
          <h3 class="font-bold text-yellow-700">Saída para Estamparia</h3>
          <p class="text-sm text-gray-700">Debita lisas, transforma em estampa.</p>
        </button>
        <button onclick="selecionarTipo('Balanço')" class="card-tipo bg-purple-100 hover:bg-purple-200">
          <h3 class="font-bold text-purple-700">Balanço</h3>
          <p class="text-sm text-gray-700">Substitui o saldo para um SKU.</p>
        </button>
        <button onclick="selecionarTipo('Pick and Packing - Retirada')" class="card-tipo bg-pink-100 hover:bg-pink-200">
          <h3 class="font-bold text-pink-700">Retirada para Expedição</h3>
          <p class="text-sm text-gray-700">Entra no fluxo de packing.</p>
        </button>
        <button onclick="selecionarTipo('Contagem Rotineira')" class="card-tipo bg-gray-100 hover:bg-gray-200">
          <h3 class="font-bold text-gray-700">Contagem Rotineira</h3>
          <p class="text-sm text-gray-700">Confirma o saldo para destino.</p>
        </button>
      </div>
    </div>

    <div id="blocoSaldos">
      <h2 class="text-lg font-semibold text-gray-800 mb-4">📊 Resumo Estoque (Top 10)</h2>

      <div id="filtrosResumoEstoque" class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-4">
        <!-- Esses elementos serão preenchidos dinamicamente com JS após carregar os dados -->
      </div>

      <button onclick="carregarResumoEstoque()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded text-sm mb-4">
        🔍 Ver Top 10 Saldo
      </button>

      <div id="tabelaResumoEstoque" class="overflow-x-auto text-sm text-gray-700"></div>
      <div class="text-xs text-gray-500 mt-2">🔎 Apenas os 10 primeiros resultados estão visíveis. Para ver tudo, acesse o dashboard completo.</div>
    </div>
  </div>
  
    <!-- 🧩 Formulário completo começa aqui -->
    <div id="formularioCompleto" class="hidden space-y-6">
      <!-- 🔄 Tipo de Movimentação -->
      <label class="block">
        Tipo de Movimentação:
        <select id="tipoMov" class="w-full p-2 border rounded">
          <option>Entrada - Pulmão</option>
          <option>Entrada - Direto para Estampar</option>
          <option>Saída - Estampar</option>
          <option>Balanço</option>
          <option>Pick and Packing - Retirada</option>
          <option>Contagem Rotineira</option>
        </select>
      </label>

      <!-- 📅 Data -->
      <label class="block">
        Data da Movimentação:
        <input type="date" id="dataRecebimento" class="w-full p-2 border rounded" />
      </label>

      <label class="block">
  Responsável:
  <select id="responsavel" class="w-full p-2 border rounded">
    <option>Stalone</option>
    <option>Léo</option>
    <option>Rafa</option>
    <option>Gu</option>
    <option>João</option>
    <option>Lucas</option>
    <option>Peu</option>
    <option>Mewtz</option>
    <option>Lucas-CEO</option>
    <option>Matheus</option>
    <option>Roginho</option>
    <option>Cris</option>
    <option>Ste</option>
    <option>Vitória</option>
    <option>Sabrina</option>
    <option>Jaque</option>
    <option>Dane</option>
    <option>Karina</option>
    <option>Dai</option>
    <option>Anderson</option>
  </select>
  <span class="ml-1 text-blue-500 cursor-help" title="Selecione o colaborador responsável pelo registro desta movimentação.">❔</span>
</label>


      <!-- 📦 Produto, Cor, Estampa, Confecção -->
      <label class="block">Produto: <select id="produto" class="w-full p-2 border rounded"></select></label>
      <label class="block">Cor: <select id="cor" class="w-full p-2 border rounded"></select></label>
      <label class="block">Estampa: <select id="estampa" class="w-full p-2 border rounded"></select></label>
      <label class="block">Confecção: <select id="confeccao" class="w-full p-2 border rounded"></select></label>

      <!-- 🎯 Destino Final -->
      <label class="block">
        Destino Final:
        <select id="destinoFinal" class="w-full p-2 border rounded">
          <option>Máquina de Silk</option>
          <option>DTF</option>
          <option>Pick And Packing</option>
          <option>Pulmão-Montanaro</option>
          <option>Pulmão-Suapé</option>
        </select>
      </label>

      <!-- 🏷️ Classificação -->
      <label class="block">
        Classificação do Produto:
        <select id="classificacaoProduto" class="w-full p-2 border rounded">
          <option value="site">Site</option>
          <option value="outlet">Outlet</option>
          <option value="shopee">Shopee</option>
          <option value="surpresa">Surpresa</option>
        </select>
      </label>

      <!-- ⚙️ Tipo de Input -->
      <fieldset class="border-t pt-4">
        <legend class="font-semibold">⚙️ Modo de Input</legend>
        <label><input type="radio" name="modoInput" value="manual" checked> Manual por tamanho</label><br />
        <label><input type="radio" name="modoInput" value="pesagem"> Pesagem por kg (10 peças)</label>
      </fieldset>

      <!-- 🧮 Entrada Manual -->
      <div id="blocoManualPorTamanho" class="border-t pt-4">
        <h3 class="font-semibold mb-2">📝 Entrada Manual por Tamanho</h3>
        <div class="grid grid-cols-5 gap-2">
          <input type="number" placeholder="Qtd P" id="manualP" class="p-2 border rounded" />
          <input type="number" placeholder="Qtd M" id="manualM" class="p-2 border rounded" />
          <input type="number" placeholder="Qtd G" id="manualG" class="p-2 border rounded" />
          <input type="number" placeholder="Qtd GG" id="manualGG" class="p-2 border rounded" />
          <input type="number" placeholder="Qtd XG" id="manualXG" class="p-2 border rounded" />
        </div>
        <button id="abrirCalculadora" class="mt-3 bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
          🧮 Usar Calculadora de Volumes
        </button>
      </div>

      <!-- 📊 Calculadora de Volumes -->
      <div id="blocoCalculadora" class="border-t pt-4 hidden">
        <h3 class="font-semibold mb-2">🧮 Calculadora por Volume</h3>
        <div id="blocoCalculadoraConteudo" class="space-y-2 mt-2"></div>
        <button onclick="somarVolumes()" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700 mt-2">
          ✅ Somar Volumes
        </button>
      </div>

      <!-- ⚖️ Pesagem -->
      <div id="blocoPesagem" class="border-t pt-4 hidden">
        <h3 class="font-semibold mb-2">⚖️ Pesagem por Tamanho</h3>
        <div class="grid grid-cols-5 gap-2">
          <input type="number" id="pcP" value="10" disabled class="p-2 border rounded bg-gray-100" />
          <input type="number" id="pcM" value="10" disabled class="p-2 border rounded bg-gray-100" />
          <input type="number" id="pcG" value="10" disabled class="p-2 border rounded bg-gray-100" />
          <input type="number" id="pcGG" value="10" disabled class="p-2 border rounded bg-gray-100" />
          <input type="number" id="pcXG" value="10" disabled class="p-2 border rounded bg-gray-100" />
        </div>
        <div class="grid grid-cols-5 gap-2 mt-2">
          <input type="number" placeholder="P - KG" id="kgP" class="p-2 border rounded" />
          <input type="number" placeholder="M - KG" id="kgM" class="p-2 border rounded" />
          <input type="number" placeholder="G - KG" id="kgG" class="p-2 border rounded" />
          <input type="number" placeholder="GG - KG" id="kgGG" class="p-2 border rounded" />
          <input type="number" placeholder="XG - KG" id="kgXG" class="p-2 border rounded" />
        </div>
        <p id="resultadoGramatura" class="text-xs text-blue-600 mt-2 italic"></p>
      </div>

            <!-- 📝 Comentários -->
      <div class="border-t pt-4">
        <label class="block font-semibold mb-1">📝 Comentários</label>
        <textarea id="comentarios" rows="2" class="w-full p-2 border rounded"
          placeholder="Observações ou detalhes adicionais..."></textarea>
      </div>

      <!-- ✅ Botões de Controle -->
      <div class="flex gap-4 mt-6">
       <button id="btnExibirResumo" onclick="exibirResumo()" class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
  📋 Exibir Resumo
</button>

        <button id="btnConfirmarResumo" onclick="confirmarMovimentacao()" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700 hidden" disabled>
          ✅ Confirmar Movimentação
        </button>
        <button onclick="voltarAoInicio()" class="bg-gray-400 text-white px-4 py-2 rounded hover:bg-gray-500">
          🔙 Voltar ao Início
        </button>
      </div>

      <!-- 📌 Resumo Visual -->
      <div id="resumoVisual" class="mt-6 p-4 bg-gray-100 border border-gray-300 rounded hidden"></div>

    </div> <!-- Fecha #formularioCompleto -->


<!-- ✅ Filtros Visuais para Resumo de Estoque -->
<div class="mt-6">
  <h2 class="text-lg font-semibold mb-2">🔎 Filtros do Top 10 Estoque</h2>
  <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-4">
    <select id="filtroProduto" class="border rounded p-2 text-sm">
      <option value="">🔍 Produto</option>
    </select>
    <select id="filtroCor" class="border rounded p-2 text-sm">
      <option value="">🎨 Cor</option>
    </select>
    <select id="filtroEstampa" class="border rounded p-2 text-sm">
      <option value="">🖼️ Estampa</option>
    </select>
    <select id="filtroTamanho" class="border rounded p-2 text-sm">
      <option value="">📏 Tamanho</option>
      <option>P</option><option>M</option><option>G</option><option>GG</option><option>XG</option>
    </select>
  </div>
  <div class="mb-2">
    <button onclick="limparFiltrosResumoEstoque()" class="bg-gray-200 hover:bg-gray-300 text-sm px-3 py-1 rounded">🔄 Limpar Filtros</button>
  </div>
  <div id="tabelaResumoEstoque" class="overflow-x-auto"></div>
</div>

  <!-- ⏬ Script com funções será incluído abaixo -->
<script>

  function selecionarTipo(tipoSelecionado) {
  const tipoInput = document.getElementById("tipoMov");
  if (tipoInput) tipoInput.value = tipoSelecionado;
  document.getElementById("selecaoTipoMovimentacao").classList.add("hidden");
  document.getElementById("formularioCompleto").classList.remove("hidden");
  document.getElementById("blocoSaldos").classList.add("hidden");
}

function voltarAoInicio() {
  document.getElementById("formularioCompleto").classList.add("hidden");
  document.getElementById("resumoVisual").classList.add("hidden");
  document.getElementById("btnConfirmarResumo").classList.add("hidden");
  document.getElementById("btnConfirmarResumo").disabled = true;
  document.getElementById("selecaoTipoMovimentacao").classList.remove("hidden");
}

function preencherDropdownsResumoEstoque(dados) {
  const preencher = (id, lista) => {
    const select = document.getElementById(id);
    if (!select || !Array.isArray(lista)) return;
    select.innerHTML = "<option value=''>Selecione</option>";
    lista.forEach(item => {
      const opt = document.createElement("option");
      opt.value = item;
      opt.textContent = item;
      select.appendChild(opt);
    });
  };

  preencher("filtroProduto", dados.produtos);
  preencher("filtroCor", dados.cores);
  preencher("filtroEstampa", dados.estampas);
  preencher("filtroTamanho", ["P", "M", "G", "GG", "XG"]);
}

function ativarEventosFiltroTabelaResumo() {
  const campos = ["filtroProduto", "filtroCor", "filtroEstampa", "filtroTamanho"];
  campos.forEach(id => {
    const el = document.getElementById(id);
    if (el) el.addEventListener("change", renderizarTabelaComFiltro);
  });
}

function limparFiltrosResumoEstoque() {
  document.getElementById("filtroProduto").value = "";
  document.getElementById("filtroCor").value = "";
  document.getElementById("filtroEstampa").value = "";
  document.getElementById("filtroTamanho").value = "";
  renderizarTabelaComFiltro();
}

  // 🔁 Carregamento inicial com handler certo para preenchimento dos dropdowns principais (produto, cor, estampa, confeccao)
  window.addEventListener("DOMContentLoaded", () => {
    google.script.run
      .withSuccessHandler(data => {
        preencherDropdowns(data);              // Preenche dropdowns do FORMULÁRIO
        preencherDropdownsResumoEstoque(data); // Preenche dropdowns de FILTRO DO TOP 10
        ativarEventosFiltroTabelaResumo();     // Eventos nos filtros
        carregarResumoEstoque();               // Inicializa a tabela com os dados
      })
      .withFailureHandler(e => alert("Erro ao carregar dropdowns: " + e.message))
      .getDropdownEstoque();
  });

let dadosMapaSKU = [];

function carregarResumoEstoque() {
  google.script.run.withSuccessHandler(resumo => {
    dadosMapaSKU = resumo;
    renderizarTabelaComFiltro();
  }).getSaldosMapaSKU();
}

function renderizarTabelaComFiltro() {
  if (!Array.isArray(dadosMapaSKU)) return;

  const produto = document.getElementById("filtroProduto")?.value?.trim();
  const cor = document.getElementById("filtroCor")?.value?.trim();
  const estampa = document.getElementById("filtroEstampa")?.value?.trim();
  const tamanho = document.getElementById("filtroTamanho")?.value?.trim();

  let resultado = [...dadosMapaSKU];

  if (produto) resultado = resultado.filter(l => l.produto === produto);
  if (cor) resultado = resultado.filter(l => l.cor === cor);
  if (estampa) resultado = resultado.filter(l => l.estampa === estampa);
  if (tamanho) resultado = resultado.filter(l => l.tamanho === tamanho);

  const tabela = document.getElementById("tabelaResumoEstoque");
  tabela.innerHTML = "";

  if (resultado.length === 0) {
    tabela.innerHTML = "<p class='text-red-500 mt-4'>⚠️ Nenhum resultado encontrado com os filtros aplicados.</p>";
    return;
  }

  const top10 = resultado.slice(0, 10);

  let html = `
    <table class="min-w-full divide-y divide-gray-200 mt-4 bg-white rounded shadow overflow-hidden">
      <thead class="bg-gray-100">
        <tr>
          <th class="px-4 py-2 text-left text-sm font-medium">SKU</th>
          <th class="px-4 py-2 text-left text-sm font-medium">Produto</th>
          <th class="px-4 py-2 text-left text-sm font-medium">Cor</th>
          <th class="px-4 py-2 text-left text-sm font-medium">Tam</th>
          <th class="px-4 py-2 text-left text-sm font-medium">Estampa</th>
          <th class="px-4 py-2 text-right text-sm font-medium">Lisa</th>
          <th class="px-4 py-2 text-right text-sm font-medium">Estampa</th>
        </tr>
      </thead>
      <tbody class="divide-y divide-gray-100">
  `;

  top10.forEach(l => {
    html += `
      <tr>
        <td class="px-4 py-2 text-xs">${l.sku}</td>
        <td class="px-4 py-2 text-xs">${l.produto}</td>
        <td class="px-4 py-2 text-xs">${l.cor}</td>
        <td class="px-4 py-2 text-xs">${l.tamanho}</td>
        <td class="px-4 py-2 text-xs">${l.estampa}</td>
        <td class="px-4 py-2 text-right text-xs">${l.saldoLisa}</td>
        <td class="px-4 py-2 text-right text-xs">${l.saldoEstampa}</td>
      </tr>
    `;
  });

  html += `</tbody></table>
  <p class="text-xs text-gray-500 mt-2">🔍 Exibindo as <strong>10 primeiras linhas</strong>. Para ver tudo, acesse o dashboard completo.</p>`;

  tabela.innerHTML = html;
}

// 🔃 Preenche os dropdowns dinâmicos vindos do backend
function preencherDropdowns(data) {
  const preencher = (id, opcoes) => {
    const select = document.getElementById(id);
    if (!select || !Array.isArray(opcoes)) return;
    select.innerHTML = "";
    opcoes.forEach(op => {
      const opt = document.createElement("option");
      opt.value = op;
      opt.textContent = op;
      select.appendChild(opt);
    });
  };

  preencher("produto", data.produtos);
  preencher("cor", data.cores);
  preencher("confeccao", data.confeccoes);
  preencher("estampa", data.estampas);
}


google.script.run.withSuccessHandler(carregarResumoEstoque).getSaldosMapaSKU();

function filtrarTabelaEstoque() {
  const filtro = document.getElementById("filtroEstoque").value.toLowerCase();
  ["corpoLisas", "corpoEstampadas"].forEach(id => {
    const linhas = document.getElementById(id).querySelectorAll("tr");
    linhas.forEach(l => {
      l.style.display = l.innerText.toLowerCase().includes(filtro) ? "" : "none";
    });
  });
}

function recalcularSaldosPainel() {
  const botao = event.target;
  botao.disabled = true;
  botao.textContent = "⏳ Recalculando...";

  google.script.run
  .withSuccessHandler(() => {
    carregarResumoEstoque();
    botao.textContent = "✅ Recalculado!";
    setTimeout(() => {
      botao.textContent = "🔄 Recalcular Saldos";
      botao.disabled = false;
    }, 3000);
  })
  .withFailureHandler(e => {
    alert("❌ Erro ao recalcular: " + e.message);
    botao.textContent = "🔄 Recalcular Saldos";
    botao.disabled = false;
  })
  .recalcularSaldosEstoque();

}



// ✅ Bloco JS3 Refatorado com Lógica Compatível ao Recalculo de Saldo

function exibirResumo() {
  try {
    const getVal = id => document.getElementById(id)?.value?.trim() || "-";
    const tamanhos = ["P", "M", "G", "GG", "XG"];
    let detalhes = "";
    tamanhos.forEach(t => {
      const qtd = parseInt(document.getElementById("manual" + t)?.value) || 0;
      detalhes += `${t}: ${qtd} pcs<br>`;
    });

    const resumoHTML = `
      <p><strong>Produto:</strong> ${getVal("produto")}</p>
      <p><strong>Cor:</strong> ${getVal("cor")}</p>
      <p><strong>Estampa:</strong> ${getVal("estampa")}</p>
      <p><strong>Destino:</strong> ${getVal("destinoFinal")}</p>
      <p><strong>Tipo:</strong> ${getVal("tipoMov")}</p>
      <p><strong>Confecção:</strong> ${getVal("confeccao")}</p>
      <p><strong>Responsável:</strong> ${getVal("responsavel")}</p>
      <p><strong>Classificação:</strong> ${getVal("classificacaoProduto")}</p>
      <p><strong>Detalhes:</strong><br>${detalhes}</p>
      <p><strong>Comentário:</strong> ${getVal("comentarios")}</p>
    `;

    console.log("🧪 RESUMO MONTADO:", resumoHTML);

    const blocoResumo = document.getElementById("resumoVisual");
    if (!blocoResumo) throw new Error("❌ Não encontrou #resumoVisual");
    blocoResumo.innerHTML = resumoHTML;
    blocoResumo.classList.remove("hidden");

    const btnConfirmar = document.getElementById("btnConfirmarResumo");
    if (!btnConfirmar) throw new Error("❌ Não encontrou #btnConfirmarResumo");
    btnConfirmar.disabled = false;
    btnConfirmar.classList.remove("hidden");

  } catch (e) {
    alert("🚨 Erro ao exibir resumo: " + e.message);
  }
}

function montarResumoMovimentacao() {
  const get = id => document.getElementById(id)?.value?.trim() || "";
  const tamanhos = ["P", "M", "G", "GG", "XG"];
  const pcsEstimadas = {};
  tamanhos.forEach(t => {
    pcsEstimadas[t] = parseInt(document.getElementById("manual" + t)?.value) || 0;
  });

  // 🔧 Captura o valor real do select (pode ter sido alterado via botão)
  const tipoMovReal = document.getElementById("tipoMov")?.value?.trim() || "";

  return {
    produto: get("produto"),
    cor: get("cor"),
    estampa: get("estampa"),
    confeccao: get("confeccao"),
    destinoFinal: get("destinoFinal"),
    tipoMov: tipoMovReal, // <-- Aqui usamos o real
    data: get("dataRecebimento"),
    responsavel: get("responsavel"),
    classificacao: get("classificacaoProduto"),
    comentario: get("comentarios"),
    pcsEstimadas
  };
}


function confirmarMovimentacao() {
  const resumo = montarResumoMovimentacao();

  const loader = document.getElementById("toastCarregando");
  const toast = document.getElementById("toastSucesso");

  loader.style.display = "block"; // ⏳ Mostra "Registrando..."

  google.script.run
    .withSuccessHandler(() => {
      google.script.run
        .withSuccessHandler(() => {
          loader.style.display = "none"; // 🔄 Esconde loader
          toast.style.display = "block"; // ✅ Mostra sucesso

          setTimeout(() => {
            toast.style.display = "none";
            voltarAoInicio();
          }, 4000);
        })
        .withFailureHandler(e => {
          loader.style.display = "none";
          alert("❌ Erro ao registrar: " + e.message);
        })
        .registrarMovimentacaoResumo();
    })
    .withFailureHandler(e => {
      loader.style.display = "none";
      alert("❌ Erro ao salvar no cache: " + e.message);
    })
    .salvarResumoNoCache(resumo);
}



</script>

</body>
</html>

// =====================================
// 📅 Renderiza o painel HTML
// =====================================
function doGet(e) {
  const template = HtmlService.createTemplateFromFile("painelEstoque");
  template.dadosDropdowns = getDropdownEstoque();
  return template.evaluate()
    .setTitle("Painel Estoque - Orbitta x Berzerk")
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

// =====================================
// 🔽 Carrega valores para os dropdowns do painel
// =====================================
function getDropdownEstoque() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaProduto = ss.getSheetByName("produto_consumo_custo");
  const abaValidacao = ss.getSheetByName("validacao_suspensa");

  if (!abaProduto || !abaValidacao) {
    throw new Error("❌ Abas 'produto_consumo_custo' ou 'validacao_suspensa' não encontradas.");
  }

  
Logger.log({
  produtos: [...new Set(abaProduto.getRange("A2:A").getValues().flat().filter(Boolean))],
  cores: [...new Set(abaValidacao.getRange("E2:E").getValues().flat().filter(Boolean))],
  confeccoes: [...new Set(abaValidacao.getRange("G2:G").getValues().flat().filter(Boolean))],
  estampas: [...new Set(abaValidacao.getRange("N2:N").getValues().flat().filter(Boolean))]
});

  return {
    produtos: [...new Set(abaProduto.getRange("A2:A").getValues().flat().filter(Boolean))],
    cores: [...new Set(abaValidacao.getRange("E2:E").getValues().flat().filter(Boolean))],
    confeccoes: [...new Set(abaValidacao.getRange("G2:G").getValues().flat().filter(Boolean))],
    estampas: [...new Set(abaValidacao.getRange("N2:N").getValues().flat().filter(Boolean))],
    tiposMovimentacao: [
      "Entrada - Pulmão",
      "Entrada - Direto para Estampar",
      "Saída - Estampar",
      "Balanço",
      "Contagem Rotineira"
    ]
  };
}
function getSaldosMapaSKU() {
  garantirCabecalhoMapaSKU(); // ✅ Garante que o cabeçalho esteja correto antes de seguir

  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("MapaSKU");
  const dados = aba.getDataRange().getValues();
  const header = dados[0].map(c => c.toString().trim().toUpperCase());

  const idxSKU = header.indexOf("SKU");
  const idxProduto = header.indexOf("PRODUTO");
  const idxCor = header.indexOf("COR");
  const idxTam = header.indexOf("TAMANHO");
  const idxEstampa = header.indexOf("ESTAMPA");
  const idxSaldoLisa = header.indexOf("SALDO LISA");
  const idxSaldoEstampa = header.indexOf("SALDO ESTAMPA");

  if (
    idxSKU === -1 ||
    idxProduto === -1 ||
    idxCor === -1 ||
    idxTam === -1 ||
    idxEstampa === -1 ||
    idxSaldoLisa === -1 ||
    idxSaldoEstampa === -1
  ) {
    throw new Error("❌ Colunas esperadas não encontradas no MapaSKU");
  }

  const resultado = [];

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    resultado.push({
      sku: linha[idxSKU] || "",
      produto: linha[idxProduto] || "",
      cor: linha[idxCor] || "",
      tamanho: linha[idxTam] || "",
      estampa: linha[idxEstampa] || "",
      saldoLisa: Number(linha[idxSaldoLisa]) || 0,
      saldoEstampa: Number(linha[idxSaldoEstampa]) || 0,
    });
  }

  return resultado;
}


// =====================================
// 📄 Cabeçalho padrão para MapaSKU
// =====================================
function garantirCabecalhoMapaSKU() {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("MapaSKU");
  const cabecalhoEsperado = ["SKU", "Produto", "Cor", "Tamanho", "Estampa", "Saldo Lisa", "Saldo Estampa", "Último Cálculo"];
  const atual = aba.getRange(1, 1, 1, cabecalhoEsperado.length).getValues()[0].map(c => c.toString().trim());
  const precisa = cabecalhoEsperado.some((col, i) => col !== atual[i]);
  if (precisa) aba.getRange(1, 1, 1, cabecalhoEsperado.length).setValues([cabecalhoEsperado]);
}


// =====================================
// 📄 Cabeçalho padrão para logs de estoque
// =====================================
const CABECALHO_PADRAO = [
  "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino", "OP", "Data",
  "Qtd Entrada", "Qtd Saída", "Tipo", "SKU", "Origem Registro", "Ultima_ocorrencia", "SKU Transformado",
  "Saldo Lisas", "Saldo Estampadas", "Ultima_atualizacao", "Confecção"
];

function garantirCabecalhoPadrao(aba) {
  const headersAtuais = aba.getRange(1, 1, 1, aba.getLastColumn()).getValues()[0];
  const precisaAtualizar = CABECALHO_PADRAO.some((col, i) => headersAtuais[i] !== col);
  if (precisaAtualizar) aba.getRange(1, 1, 1, CABECALHO_PADRAO.length).setValues([CABECALHO_PADRAO]);
}

// =====================================
// ✅ Funções comentadas em profundidade (continuação)
// =====================================
// As funções a seguir serão comentadas linha a linha:
// - registrarEntradaEstoque()
// - registrarBalancoBlitz()
// - registrarContagemRotineira()
// - registrarMovimentacaoResumo()
// - e demais auxiliares


// =====================================
// 📝 Registra uma nova ENTRADA no estoque
// =====================================
function registrarEntradaEstoque(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();

  // 🗂️ Referência às abas necessárias
  const logEstoque = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");
  const abaPulmao = ss.getSheetByName("Entradas no Pulmão");
  const abaEstampar = ss.getSheetByName("Entradas para Estampar");

  // Define para qual aba o registro visual será feito, com base no tipo de movimentação
  const abaDestino = dados.tipoMov.includes("Pulmão") ? abaPulmao : abaEstampar;

  const agora = new Date();
  const { produto, cor, confeccao, responsavel, dataRecebimento, tipoMov, destinoFinal, estampa, pcsEstimadas } = dados;

  const tamanhos = ["P", "M", "G", "GG", "XG"];
  const fallbackEstampa = estampa || "LISA";

  const linhasEstoque = []; // registros visuais (aba destino)
  const linhasLog = [];     // registros de log (aba log)

  // ✅ Garante que o cabeçalho do log exista e tenha colunas padrão
  if (logEstoque.getLastRow() === 0) {
    logEstoque.appendRow([
      "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino",
      "OP", "Data Registro", "Qtd Entrada", "Qtd Saída", "Tipo Movimentação",
      "SKU", "Saldo", "Fonte", "OBS"
    ]);
  } else {
    const cab = logEstoque.getRange(1, 1, 1, logEstoque.getLastColumn()).getValues()[0];
    if (!cab.includes("OBS")) logEstoque.getRange(1, cab.length + 1).setValue("OBS");
  }

  // 🧮 Para cada tamanho, gera linha de entrada se houver quantidade
  tamanhos.forEach(t => {
    const qtd = pcsEstimadas?.[t] || 0;
    if (qtd <= 0) return;

    // 🔍 Busca SKU oficial
    const sku = buscarSKUOficialComCache(produto, cor, fallbackEstampa, t);
    if (!sku) {
      Logger.log(`❌ SKU não encontrado para ${produto} ${cor} ${fallbackEstampa} ${t}`);
      return;
    }

    const destinoNorm = normalizarDestino(destinoFinal);

    // 📦 Linha do log de estoque
    linhasLog.push([
      produto,
      cor,
      t,
      fallbackEstampa,
      responsavel,
      tipoMov,
      destinoNorm || "-",
      "-",
      agora,
      tipoMov.includes("Saída") ? "" : qtd,
      tipoMov.includes("Saída") ? qtd : "",
      tipoMov.toUpperCase(),
      sku,
      tipoMov.includes("Saída") ? 0 : qtd,
      "WEBAPP",
      ""
    ]);

    // 📋 Linha visual (aba Pulmão ou Estampar)
    if (abaDestino) {
      linhasEstoque.push([
        agora,
        produto,
        cor,
        t,
        fallbackEstampa,
        responsavel,
        confeccao || "-",
        destinoNorm || "-",
        tipoMov,
        qtd,
        sku
      ]);
    }
  });

  // ✍️ Escreve dados nas abas
    if (linhasLog.length > 0) {
    logEstoque.getRange(logEstoque.getLastRow() + 1, 1, linhasLog.length, linhasLog[0].length).setValues(linhasLog);
  }

  // 🔄 Recalcula os saldos após entrada
  recalcularSaldosEstoque();

  // ✅ Retorna confirmação para o frontend
  return "OK";
}


  

// =====================================
// 📦 Registra um BALANÇO Blitz 5S
// =====================================
function registrarBalancoBlitz(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const logEstoque = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");
  const logBalanco = ss.getSheetByName("Log Balanço Blitz") || ss.insertSheet("Log Balanço Blitz");

  const dataRegistro = Utilities.formatDate(new Date(), 'GMT-3', 'dd/MM/yyyy');

  // 📋 Cabeçalho padrão das abas de log
  const cabecalho = [
    "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino", "OP",
    "Data Registro", "Qtd Entrada", "Qtd Saída", "Tipo Movimentação", "SKU",
    "Saldo", "Origem Registro", "Última ocorrência", "OBS"
  ];

  if (logEstoque.getLastRow() === 0) logEstoque.appendRow(cabecalho);
  if (logBalanco.getLastRow() === 0) logBalanco.appendRow(cabecalho);

  if (!dados || !dados.length) {
    Logger.log("⚠️ Nenhum dado recebido para balanço.");
    return;
  }

  dados.forEach(item => {
    const produto = item.produto || '';
    const cor = item.cor || '';
    const tamanho = item.tamanho || '';
    const estampa = item.estampa || 'LISA';
    const saldo = item.saldo || 0;
    const destino = normalizarDestino(item.destino || 'Pulmão - Montanaro');
    const responsavel = item.responsavel || '-';

    // 🔍 Busca o SKU oficial com fallback
    const sku = buscarSKUOficialComCache(produto, cor, estampa, tamanho) || item.sku || '';

    const novaLinha = [
      produto,
      cor,
      tamanho,
      estampa,
      responsavel,
      '-',
      destino,
      '-',
      dataRegistro,
      saldo,
      '',
      'BALANÇO',
      sku,
      saldo,
      'WEBAPP',
      dataRegistro,
      sku ? "" : "❌ SKU não encontrado"
    ];

    logEstoque.appendRow(novaLinha);
    logBalanco.appendRow(novaLinha);
  });

  Logger.log(`✅ ${dados.length} entradas registradas via Balanço Blitz.`);
}

// =====================================
// 🔄 Registra uma CONTAGEM ROTINEIRA com ajuste de saldo
// =====================================
function registrarContagemRotineira(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");

  const agora = new Date();
  const cabecalho = [
    "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino",
    "OP", "Data Registro", "Qtd Entrada", "Qtd Saída", "Tipo Movimentação",
    "SKU", "Saldo", "Origem Registro", "OBS"
  ];

  if (abaLog.getLastRow() === 0) abaLog.appendRow(cabecalho);

  if (!dados || !dados.length) {
    Logger.log("⚠️ Nenhum dado recebido para contagem.");
    return;
  }

  // 📦 Gera mapa de saldos atuais por SKU|DESTINO
  const mapaSaldos = gerarMapaSaldosEstoque();

  const novasLinhas = [];

  dados.forEach(item => {
    const { produto, cor, tamanho, estampa, destino, contagem, responsavel } = item;

    const estampaFinal = estampa || "LISA";
    const destinoFinal = normalizarDestino(destino || "Pulmão");
    const sku = buscarSKUOficialComCache(produto, cor, estampaFinal, tamanho);
    if (!sku) return;

    const chave = `${sku}|${destinoFinal}`;
    const saldoAtual = mapaSaldos[chave] || 0;
    const diferenca = Number(contagem) - Number(saldoAtual);

    if (diferenca === 0) return; // Nenhuma diferença, pula

    const entrada = diferenca > 0 ? diferenca : "";
    const saida = diferenca < 0 ? -diferenca : "";

    novasLinhas.push([
      produto,
      cor,
      tamanho,
      estampaFinal,
      responsavel || "-",
      "-",
      destinoFinal,
      "-",
      agora,
      entrada,
      saida,
      "CONTAGEM ROTINEIRA",
      sku,
      contagem,
      "WEBAPP",
      `🔁 Ajuste via contagem. Saldo anterior: ${saldoAtual}, contagem: ${contagem}`
    ]);
  });

  if (novasLinhas.length > 0) {
    abaLog.getRange(abaLog.getLastRow() + 1, 1, novasLinhas.length, novasLinhas[0].length).setValues(novasLinhas);
    Logger.log(`✅ ${novasLinhas.length} ajustes registrados por contagem rotineira.`);
  } else {
    Logger.log("ℹ️ Nenhum ajuste necessário.");
  }

  // 🔄 Atualiza saldos finais
  recalcularSaldosEstoque();
}

// ✅ Refatoração central: Corrige rota de "Saída - Estampar" e garante visibilidade no painel

function registrarMovimentacaoResumo() {
  const cache = CacheService.getScriptCache();
  const valor = cache.get("resumoMovimentacao");
  if (!valor) throw new Error("❌ Cache expirado ou não encontrado. Volte e exiba o resumo novamente.");

  const resumo = JSON.parse(valor);

  if (resumo.tipoMov.includes("Balanço")) {
    const linhasBalanco = Object.entries(resumo.pcsEstimadas)
      .filter(([_tamanho, qtd]) => qtd > 0)
      .map(([tamanho, qtd]) => ({
        produto: resumo.produto,
        cor: resumo.cor,
        tamanho,
        estampa: resumo.estampa,
        saldo: qtd,
        destino: resumo.destinoFinal,
        sku: buscarSKUOficialComCache(resumo.produto, resumo.cor, resumo.estampa, tamanho),
        responsavel: resumo.responsavel
      }));
    return registrarBalancoBlitz(linhasBalanco);
  }

  if (resumo.tipoMov.includes("Pick and Packing")) {
    const linhasPick = Object.entries(resumo.pcsEstimadas)
      .filter(([_tamanho, qtd]) => qtd > 0)
      .map(([tamanho, qtd]) => ({
        produto: resumo.produto,
        cor: resumo.cor,
        tamanho,
        estampa: resumo.estampa,
        classificacao: resumo.destinoFinal,
        quantidade: qtd,
        local: resumo.confeccao,
        saldo: qtd,
        responsavel: resumo.responsavel
      }));
    return registrarRetiradaPickAndPacking(linhasPick);
  }

  if (resumo.tipoMov.includes("Saída - Estampar")) {
    const ss = SpreadsheetApp.getActiveSpreadsheet();
    const logEstoque = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");
    const logEstampadas = ss.getSheetByName("log_estampadas") || ss.insertSheet("log_estampadas");
    const agora = new Date();

    const linhasLisa = [];
    const linhasEstampa = [];

    Object.entries(resumo.pcsEstimadas).forEach(([tamanho, qtd]) => {
      if (!qtd || qtd <= 0) return;
      const estampaFinal = resumo.estampa || "LISA";

      const skuLisa = buscarSKUOficialComCache(resumo.produto, resumo.cor, "LISA", tamanho);
      const skuEstampa = buscarSKUOficialComCache(resumo.produto, resumo.cor, estampaFinal, tamanho);
      if (!skuLisa || !skuEstampa) return;

      const destino = normalizarDestino(resumo.destinoFinal);

      linhasLisa.push([
        resumo.produto,
        resumo.cor,
        tamanho,
        "LISA",
        resumo.responsavel,
        "SAÍDA - ESTAMPAR",
        destino,
        "-",
        agora,
        "",
        qtd,
        "SAÍDA - ESTAMPAR",
        skuLisa,
        "",
        "WEBAPP",
        "Transformado em: " + skuEstampa
      ]);

      linhasEstampa.push([
        resumo.produto,
        resumo.cor,
        tamanho,
        estampaFinal,
        resumo.responsavel,
        "ENTRADA - TRANSFORMAÇÃO",
        destino,
        "-",
        agora,
        qtd,
        "",
        "ENTRADA - TRANSFORMAÇÃO",
        skuEstampa,
        "",
        "WEBAPP",
        "Origem: " + skuLisa
      ]);
    });

    if (linhasLisa.length > 0) logEstoque.getRange(logEstoque.getLastRow() + 1, 1, linhasLisa.length, linhasLisa[0].length).setValues(linhasLisa);
    if (linhasEstampa.length > 0) logEstoque.getRange(logEstoque.getLastRow() + 1, 1, linhasEstampa.length, linhasEstampa[0].length).setValues(linhasEstampa);
    if (linhasEstampa.length > 0) logEstampadas.getRange(logEstampadas.getLastRow() + 1, 1, linhasEstampa.length, linhasEstampa[0].length).setValues(linhasEstampa);

    recalcularSaldosEstoque();
    cache.remove("resumoMovimentacao");
    return "OK";
  }

  return registrarEntradaEstoque(resumo);
}

// =====================================
// 🔍 Normaliza texto removendo acentos e espaços
// =====================================
function normalizarTexto(str) {
  if (!str) return "";
  return str.toString()
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "")
    .replace(/[^\w\s]/gi, "")
    .replace(/\s+/g, "")
    .toUpperCase();
}


// =====================================
// 📌 Normaliza destinos para nomes-padrão
// =====================================
function normalizarDestino(destino) {
  const d = (destino || "").toString().toUpperCase();
  if (d === "DTF" || d === "MÁQUINA DE SILK") return "Pulmão-Suapé";
  return destino;
}

// =====================================
// 🔍 Busca SKU oficial com cache e fallback para Lisa
// =====================================
function buscarSKUOficialComCache(produto, cor, estampa, tamanho) {
  if (!produto || !cor || !tamanho) return null;
  if (!estampa || estampa.toString().trim() === "") estampa = "Lisa";

  const norm = txt => normalizarTexto(txt);
  const chaveBusca = `${norm(produto)}|${norm(cor)}|${norm(estampa)}|${norm(tamanho)}`;

  const cache = prepararCacheSKUs();
  const encontrado = cache.find(l =>
    `${norm(l.produto)}|${norm(l.cor)}|${norm(l.estampa)}|${norm(l.tamanho)}` === chaveBusca
  );

  return encontrado ? encontrado.sku : null;
}

// =====================================
// 🧱 Prepara cache de SKUs a partir da aba 'skus_internos'
// =====================================
function prepararCacheSKUs() {
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("skus_internos");
  const dados = aba.getDataRange().getValues();
  const cab = dados[0].map(h => h.toString().trim().toUpperCase());

  return dados.slice(1).map(l => ({
    produto: l[cab.indexOf("PRODUTO")],
    cor:     l[cab.indexOf("COR")],
    estampa: l[cab.indexOf("ESTAMPA")],
    tamanho: l[cab.indexOf("TAMANHO")],
    sku:     l[cab.indexOf("SKU_INTERNO")]
  }));
}

// =====================================
// 🧮 Gera mapa de saldos atuais a partir do log
// =====================================
function gerarMapaSaldosEstoque() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const aba = ss.getSheetByName("Log Estoque Total");
  const dados = aba.getDataRange().getValues();
  const cab = dados[0].map(h => h.toString().trim().toUpperCase());

  const idxSKU = cab.indexOf("SKU");
  const idxDestino = cab.indexOf("DESTINO");
  const idxTipo = cab.indexOf("TIPO");
  const idxQtdEntrada = cab.indexOf("QTD ENTRADA");
  const idxQtdSaida = cab.indexOf("QTD SAÍDA");

  if ([idxSKU, idxDestino, idxTipo, idxQtdEntrada, idxQtdSaida].some(i => i === -1)) {
    throw new Error("❌ Colunas obrigatórias não encontradas no Log Estoque Total");
  }

  const mapa = {};

  for (let i = 1; i < dados.length; i++) {
    const linha = dados[i];
    const sku = linha[idxSKU];
    const destino = linha[idxDestino];
    const entrada = parseFloat(linha[idxQtdEntrada] || 0);
    const saida = parseFloat(linha[idxQtdSaida] || 0);

    const chave = `${sku}||${destino}`;
    if (!mapa[chave]) mapa[chave] = 0;
    mapa[chave] += entrada - saida;
  }

  return mapa; // Exemplo: { "OVRPRTLSAP||Pulmão-Montanaro": 3600 }
}

// ✅ Backend - Corrigindo função ausente salvarResumoNoCache()

function salvarResumoNoCache(resumo) {
  const cache = CacheService.getScriptCache();
  if (!resumo || typeof resumo !== "object") {
    throw new Error("❌ Resumo inválido ou ausente.");
  }

  const chave = "resumoMovimentacao";
  const valor = JSON.stringify(resumo);

  cache.put(chave, valor, 600); // Armazena por 10 minutos
  return true;
}

// ✅ Backend - Corrigindo função ausente salvarResumoNoCache()

function salvarResumoNoCache(resumo) {
  const cache = CacheService.getScriptCache();
  if (!resumo || typeof resumo !== "object") {
    throw new Error("❌ Resumo inválido ou ausente.");
  }

  const chave = "resumoMovimentacao";
  const valor = JSON.stringify(resumo);

  cache.put(chave, valor, 600); // Armazena por 10 minutos
  return true;
}

// ✅ Função complementar para registrar movimentação a partir do cache
function registrarMovimentacaoResumo() {
  const cache = CacheService.getScriptCache();
  const valor = cache.get("resumoMovimentacao");
  if (!valor) throw new Error("❌ Cache expirado ou não encontrado. Volte e exiba o resumo novamente.");

  const resumo = JSON.parse(valor);

  // Simples roteamento com base no tipo de movimentação
  if (resumo.tipoMov.includes("Balanço")) {
    const linhasBalanco = Object.entries(resumo.pcsEstimadas)
      .filter(([_tamanho, qtd]) => qtd > 0)
      .map(([tamanho, qtd]) => ({
        produto: resumo.produto,
        cor: resumo.cor,
        tamanho,
        estampa: resumo.estampa,
        saldo: qtd,
        destino: resumo.destinoFinal,
        sku: buscarSKUOficialComCache(resumo.produto, resumo.cor, tamanho),
        responsavel: resumo.responsavel
      }));
    return registrarBalancoBlitz(linhasBalanco);
  }

  if (resumo.tipoMov.includes("Pick and Packing")) {
    const linhasPick = Object.entries(resumo.pcsEstimadas)
      .filter(([_tamanho, qtd]) => qtd > 0)
      .map(([tamanho, qtd]) => ({
        produto: resumo.produto,
        cor: resumo.cor,
        tamanho,
        estampa: resumo.estampa,
        classificacao: resumo.destinoFinal,
        quantidade: qtd,
        local: resumo.confeccao,
        saldo: qtd,
        responsavel: resumo.responsavel
      }));
    return registrarRetiradaPickAndPacking(linhasPick);
  }

  // Entrada comum
  return registrarEntradaEstoque(resumo);
}

// 🔧 Monta o resumo da movimentação a partir dos campos preenchidos no painel
function montarResumoMovimentacao() {
  const get = id => document.getElementById(id)?.value?.trim() || "";
  const tamanhos = ["P", "M", "G", "GG", "XG"];
  const pcsEstimadas = {};

  tamanhos.forEach(t => {
    pcsEstimadas[t] = parseInt(document.getElementById("manual" + t)?.value) || 0;
  });

  return {
    produto: get("produto"),
    cor: get("cor"),
    tamanho: "-", // Não usado diretamente, pois usamos pcs por tamanho
    estampa: get("estampa"),
    confeccao: get("confeccao"),
    destinoFinal: get("destinoFinal"),
    tipoMov: get("tipoMov"),
    data: get("dataRecebimento"),
    responsavel: get("responsavel"),
    classificacao: get("classificacaoProduto"),
    comentario: get("comentarios"),
    pcsEstimadas: pcsEstimadas
  };
}


function montarLinhasPorTamanho(resumo) {
  const tamanhos = ["P", "M", "G", "GG", "XG"];
  return tamanhos.map(t => {
    const qtd = resumo.pcsEstimadas[t] || 0;
    if (qtd <= 0) return null;
const estampa = resumo.estampa || "LISA";
const skuBase = buscarSKUOficialComCache(resumo.produto, resumo.cor, estampa, t);
if (!skuBase) throw new Error(`❌ SKU não encontrado para: ${resumo.produto} | ${resumo.cor} | ${estampa} | ${t}`);


    return {
      produto: resumo.produto,
      cor: resumo.cor,
      tamanho: t,
      estampa: resumo.estampa,
      destino: resumo.destinoFinal,
      tipoMov: resumo.tipoMov,
      quantidade: qtd,
      classificacao: resumo.classificacao,
      confeccao: resumo.confeccao,
      responsavel: resumo.responsavel,
      data: resumo.data,
      comentario: resumo.comentario,
      sku: skuBase
    };
  }).filter(Boolean);
}

// Configurações do Supabase
const SUPABASE_URL = 'https://ikgmzwqlflzohbqomrfa.supabase.co';
const API_KEY = PropertiesService.getScriptProperties().getProperty('SUPABASE_API_KEY') || 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImlrZ216d3FsZmx6b2hicW9tcmZhIiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTc1MDcwMTg2MSwiZXhwIjoyMDY2Mjc3ODYxfQ.AwDmZFs3JqJHDX3z7SbKRUu4YKwqIYheZZeBwCByjGE';

/**
 * Salva a API key nas propriedades do script (execute esta função uma vez)
 */
function salvarApiKey(apiKey) {
  PropertiesService.getScriptProperties().setProperty('SUPABASE_API_KEY', apiKey);
  Logger.log('API Key salva com sucesso!');
}

/**
 * Normaliza nomes de colunas para snake_case
 */
function normalizarNome(coluna) {
  if (!coluna) return '';
  return coluna
    .toString()
    .trim()
    .normalize("NFD").replace(/[\u0300-\u036f]/g, "") // Remove acentos
    .replace(/[\s\/\-]+/g, "_") // Substitui espaços, barras e hífens por underscore
    .replace(/[^a-zA-Z0-9_]/g, "") // Remove caracteres especiais
    .toLowerCase();
}

/**
 * Verifica se uma coluna está vazia
 */
function colunaEstaVazia(dados, indiceColuna) {
  for (let linha = 1; linha < dados.length; linha++) {
    if (dados[linha][indiceColuna] && dados[linha][indiceColuna].toString().trim() !== '') {
      return false;
    }
  }
  return true;
}

/**
 * Filtra colunas válidas
 */
function filtrarColunasValidas(dados) {
  const headers = dados[0];
  return headers.map((header, i) => ({
    indice: i,
    headerOriginal: header,
    headerNormalizado: normalizarNome(header)
  })).filter(col =>
    col.headerNormalizado && !colunaEstaVazia(dados, col.indice)
  );
}

/**
 * Envia dados de uma aba para o Supabase
 */
function enviarAbaParaSupabase(abaNome, tabelaDestino) {
  const planilha = SpreadsheetApp.getActiveSpreadsheet();
  
  // Listar todas as abas disponíveis para debug
  const todasAbas = planilha.getSheets().map(sheet => sheet.getName());
  Logger.log(`Abas disponíveis: ${todasAbas.join(', ')}`);
  
  const aba = planilha.getSheetByName(abaNome);
  
  if (!aba) {
    Logger.log(`Aba '${abaNome}' não encontrada. Verifique o nome exato.`);
    return {sucesso: false, mensagem: `Aba '${abaNome}' não encontrada. Verifique o nome exato.`};
  }
  
  const dados = aba.getDataRange().getValues();
  
  if (dados.length < 2) {
    Logger.log(`Aba '${abaNome}' sem dados suficientes.`);
    return {sucesso: false, mensagem: `Aba '${abaNome}' sem dados suficientes.`};
  }
  
  const colunasValidas = filtrarColunasValidas(dados);
  
  if (colunasValidas.length === 0) {
    Logger.log(`Aba '${abaNome}' sem colunas válidas.`);
    return {sucesso: false, mensagem: `Aba '${abaNome}' sem colunas válidas.`};
  }
  
  // Verificar se a tabela existe antes de tentar inserir
  const verificarTabela = {
    method: 'get',
    contentType: 'application/json',
    headers: {
      apikey: API_KEY,
      Authorization: 'Bearer ' + API_KEY,
      Prefer: 'count=exact'
    },
    muteHttpExceptions: true
  };
  
  try {
    const endpointVerificacao = `${SUPABASE_URL}/rest/v1/${tabelaDestino}?limit=1`;
    const respostaVerificacao = UrlFetchApp.fetch(endpointVerificacao, verificarTabela);
    
    if (respostaVerificacao.getResponseCode() !== 200) {
      Logger.log(`Tabela '${tabelaDestino}' não encontrada ou sem acesso.`);
      return {sucesso: false, mensagem: `Tabela '${tabelaDestino}' não encontrada ou sem acesso.`};
    }
  } catch (e) {
    Logger.log(`Erro ao verificar tabela '${tabelaDestino}': ${e}`);
    return {sucesso: false, mensagem: `Erro ao verificar tabela '${tabelaDestino}': ${e}`};
  }
  
  let sucessos = 0, erros = 0;
  const errosDetalhes = [];
  const endpoint = `${SUPABASE_URL}/rest/v1/${tabelaDestino}`;
  
  // Processar em lotes para melhor desempenho
  const TAMANHO_LOTE = 20;
  const totalLinhas = dados.length - 1; // Excluindo cabeçalho
  
  for (let inicio = 1; inicio <= totalLinhas; inicio += TAMANHO_LOTE) {
    const fim = Math.min(inicio + TAMANHO_LOTE, dados.length);
    const lote = [];
    
    for (let i = inicio; i < fim; i++) {
      const linha = dados[i];
      const payload = {};
      
      // Verificar se a linha tem pelo menos um valor não vazio
      let temValor = false;
      
      colunasValidas.forEach(col => {
        const valor = linha[col.indice];
        if (valor !== undefined && valor !== null && valor.toString().trim() !== '') {
          payload[col.headerNormalizado] = valor;
          temValor = true;
        }
      });
      
      if (temValor && Object.keys(payload).length > 0) {
        lote.push(payload);
      }
    }
    
    if (lote.length === 0) continue;
    
    const options = {
      method: 'post',
      contentType: 'application/json',
      headers: {
        apikey: API_KEY,
        Authorization: 'Bearer ' + API_KEY,
        Prefer: 'return=minimal'
      },
      payload: JSON.stringify(lote),
      muteHttpExceptions: true
    };
    
    try {
      const response = UrlFetchApp.fetch(endpoint, options);
      const code = response.getResponseCode();
      
      if (code >= 200 && code < 300) {
        sucessos += lote.length;
      } else {
        erros += lote.length;
        const erro = `Erro no lote ${inicio}-${fim-1}: ${code} - ${response.getContentText()}`;
        Logger.log(erro);
        errosDetalhes.push(erro);
      }
    } catch (e) {
      erros += lote.length;
      const erro = `Erro na requisição do lote ${inicio}-${fim-1}: ${e}`;
      Logger.log(erro);
      errosDetalhes.push(erro);
    }
  }
  
  const mensagem = `Aba '${abaNome}': ${sucessos} linhas enviadas, ${erros} erros.`;
  Logger.log(mensagem);
  
  return {
    sucesso: erros === 0,
    mensagem: mensagem,
    sucessos: sucessos,
    erros: erros,
    errosDetalhes: errosDetalhes
  };
}

/**
 * Mapeamento de abas para tabelas Supabase
 * ATUALIZADO com os nomes exatos das abas da sua planilha
 */
function enviarTodasAbasParaSupabase() {
  // Mapeamento ATUALIZADO com os nomes exatos das abas
  const mapeamento = {
    // Nomes exatos das abas -> tabelas no Supabase
    'log_corte': 'logs_corte_importados',
    'Log Estoque Total': 'log_estoque_total',
    'entrada_destinacao_tecido': 'entrada_destinacao_tecido',
    'log_confeccao': 'log_confeccao'
    // Removido o Tiny conforme solicitado
  };
  
  const resultados = {};
  
  Object.keys(mapeamento).forEach(aba => {
    const tabela = mapeamento[aba];
    Logger.log(`Iniciando envio: Aba '${aba}' → Tabela '${tabela}'`);
    resultados[aba] = enviarAbaParaSupabase(aba, tabela);
  });
  
  // Exibir resumo nos logs (sem usar UI)
  let mensagemFinal = "Resumo da sincronização:\n\n";
  Object.keys(resultados).forEach(aba => {
    const resultado = resultados[aba];
    mensagemFinal += `${aba}: ${resultado.sucesso ? 'Sucesso' : 'Falha'} - ${resultado.mensagem}\n`;
  });
  
  Logger.log(mensagemFinal);
  
  return resultados;
}

/**
 * Adiciona menu no Google Sheets
 */
function onOpen() {
  try {
    const ui = SpreadsheetApp.getUi();
    ui.createMenu('📤 Supabase Sync')
      .addItem('Enviar todas as abas', 'executarEnvioComUI')
      .addSeparator()
      .addItem('Configurar API Key', 'mostrarDialogoApiKey')
      .addItem('Verificar nomes das abas', 'mostrarNomesAbas')
      .addToUi();
  } catch (e) {
    Logger.log('Erro ao criar menu: ' + e);
    // Continua silenciosamente se estiver em um contexto sem UI
  }
}

/**
 * Wrapper para enviarTodasAbasParaSupabase que mostra resultado na UI
 */
function executarEnvioComUI() {
  try {
    const resultados = enviarTodasAbasParaSupabase();
    
    // Preparar mensagem para UI
    let mensagemFinal = "Resumo da sincronização:\n\n";
    Object.keys(resultados).forEach(aba => {
      const resultado = resultados[aba];
      mensagemFinal += `${aba}: ${resultado.sucesso ? '✅' : '❌'} ${resultado.mensagem}\n`;
    });
    
    // Mostrar mensagem ao usuário
    SpreadsheetApp.getUi().alert(mensagemFinal);
  } catch (e) {
    Logger.log('Erro ao executar envio: ' + e);
    try {
      SpreadsheetApp.getUi().alert('Erro ao executar envio: ' + e);
    } catch (uiError) {
      // Ignora erro de UI se estiver em contexto sem UI
    }
  }
}

/**
 * Mostra diálogo para configurar API Key
 */
function mostrarDialogoApiKey() {
  const ui = SpreadsheetApp.getUi();
  const result = ui.prompt(
    'Configurar API Key do Supabase',
    'Insira sua API Key (service_role):',
    ui.ButtonSet.OK_CANCEL
  );
  
  if (result.getSelectedButton() == ui.Button.OK) {
    const apiKey = result.getResponseText();
    if (apiKey && apiKey.trim() !== '') {
      salvarApiKey(apiKey);
      ui.alert('API Key salva com sucesso!');
    } else {
      ui.alert('API Key inválida. Nenhuma alteração foi feita.');
    }
  }
}

/**
 * Mostra os nomes exatos das abas disponíveis
 */
function mostrarNomesAbas() {
  const planilha = SpreadsheetApp.getActiveSpreadsheet();
  const abas = planilha.getSheets().map(sheet => sheet.getName());
  
  const ui = SpreadsheetApp.getUi();
  ui.alert('Nomes das abas disponíveis:\n\n' + abas.join('\n'));
}

/**
 * Função para ser executada via gatilho de tempo
 * Pode ser configurada para rodar automaticamente
 */
function sincronizacaoAutomatica() {
  // Esta função pode ser configurada como um gatilho para execução automática
  // Vá para Editar > Acionadores do projeto atual para configurar
  return enviarTodasAbasParaSupabase();
}

function sincronizarPedidosTinyComPaginacao(token) {
  const pedidos = [];
  let pagina = 1;
  let totalPaginas = 1; // será atualizado após primeira chamada

  do {
    const url = `https://api.tiny.com.br/api2/pedidos.pesquisa.php?token=${token}&formato=json&pagina=${pagina}`;
    const resposta = UrlFetchApp.fetch(url, { muteHttpExceptions: true });
    const json = JSON.parse(resposta.getContentText());

    if (json.retorno.status !== "OK") {
      Logger.log("❌ Erro na chamada da API do Tiny: " + JSON.stringify(json.retorno));
      break;
    }

    const pedidosPagina = json.retorno.pedidos || [];

    pedidosPagina.forEach(p => {
      const pedido = p.pedido;
      pedidos.push({
        numero: pedido.numero,
        nome: pedido.nome,
        situacao: pedido.situacao,
        data_pedido: pedido.data_pedido,
        codigo_rastreamento: pedido.codigo_rastreamento,
        numero_ecommerce: pedido.numero_ecommerce,
        valor: pedido.valor,
        data_prevista: pedido.data_prevista
      });
    });

    totalPaginas = parseInt(json.retorno.numero_paginas) || 1;
    pagina++;

  } while (pagina <= totalPaginas);

  Logger.log(`✅ ${pedidos.length} pedidos sincronizados com sucesso.`);

  return pedidos;
}


<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>📦 Painel Picker - Filtro Dinâmico</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      padding: 1rem;
      background-color: #f9f9f9;
    }
    h1 {
      background-color: #facc15;
      color: #000;
      padding: 0.5rem 1rem;
      text-align: center;
      font-size: 1.5rem;
      border-radius: 8px;
    }
    .filtros {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      margin: 1rem 0;
    }
    select, input[type="date"] {
      padding: 0.5rem;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
      flex: 1 1 45%;
    }
    .card {
      background-color: white;
      margin: 1rem 0;
      padding: 1rem;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .card-header {
      font-size: 1.1rem;
      font-weight: bold;
      margin-bottom: 0.5rem;
    }
    .card-body {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    .actions {
      display: flex;
      justify-content: space-between;
      gap: 0.5rem;
    }
    .btn {
      flex: 1;
      padding: 0.5rem 1rem;
      font-size: 1rem;
      background-color: #16a34a;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .btn.falta {
      background-color: #dc2626;
    }
    .btn:disabled {
      background-color: #9ca3af;
    }
  </style>
</head>
<body>
  <h1>Painel de Separacão - Picker</h1>

  <div class="filtros">
    <input type="date" id="filtroData" />
    <select id="filtroProduto">
      <option value="">Produto</option>
    </select>
    <select id="filtroCor">
      <option value="">Cor</option>
    </select>
    <select id="filtroEstampa">
      <option value="">Estampa</option>
    </select>
    <select id="filtroTamanho">
      <option value="">Tamanho</option>
      <option value="P">P</option>
      <option value="M">M</option>
      <option value="G">G</option>
      <option value="GG">GG</option>
      <option value="XG">XG</option>
    </select>
  </div>

  <div id="listaSeparacao"></div>

  <label class="block text-sm font-medium text-gray-700 mt-4">Classificação</label>
<select id="selectClassificacao" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm">
  <option value="">-- Selecione --</option>
  <option value="site">Site</option>
  <option value="outlet">Outlet</option>
  <option value="shopee">Shopee</option>
  <option value="surpresa">Surpresa</option>
</select>


  <script>
    const lista = [
      { produto: 'OVERSIZED', cor: 'Caqui', estampa: 'Leg Day', tamanho: 'P', qtd: 30 },
      { produto: 'OVERSIZED', cor: 'Caqui', estampa: 'Olympia', tamanho: 'P', qtd: 25 },
      { produto: 'OVERSIZED', cor: 'Caqui', estampa: 'Myth', tamanho: 'P', qtd: 20 },
      { produto: 'OVERSIZED', cor: 'Caqui', estampa: 'Behind', tamanho: 'P', qtd: 10 },
    ];

function registrarSeparacao(index, status) {
  const usuario = prompt("Informe seu nome:");
  if (!usuario) return;

  const item = lista[index];
  const classificacao = document.getElementById('selectClassificacao').value || '-';

  google.script.run.registrarRetiradaPickAndPacking([{
    produto: item.produto,
    cor: item.cor,
    estampa: item.estampa,
    tamanho: item.tamanho,
    quantidade: item.qtd,
    responsavel: usuario,
    classificacao: classificacao,
    local: 'Separação WebApp',
    saldo: ''
  }]);

  alert(`${status === 'separado' ? '✅' : '❌'} ${status.toUpperCase()}: ${item.estampa} ${item.tamanho} por ${usuario}`);
  document.getElementById(`btn-sep-${index}`).disabled = true;
  document.getElementById(`btn-falta-${index}`).disabled = true;
}


    function aplicarFiltros() {
      const data = document.getElementById('filtroData').value;
      const produto = document.getElementById('filtroProduto').value;
      const cor = document.getElementById('filtroCor').value;
      const estampa = document.getElementById('filtroEstampa').value;
      const tamanho = document.getElementById('filtroTamanho').value;

      const container = document.getElementById("listaSeparacao");
      container.innerHTML = "";

      lista.filter(item => {
        return (!produto || item.produto === produto) &&
               (!cor || item.cor === cor) &&
               (!estampa || item.estampa === estampa) &&
               (!tamanho || item.tamanho === tamanho);
      }).forEach((item, i) => {
        container.innerHTML += `
          <div class="card">
            <div class="card-header">${item.produto} - ${item.estampa} - ${item.tamanho}</div>
            <div class="card-body">
              <div>Qtd a separar: <strong>${item.qtd}</strong></div>
              <div class="actions">
                <button class="btn" id="btn-sep-${i}" onclick="registrarSeparacao(${i}, 'separado')">Separado</button>
                <button class="btn falta" id="btn-falta-${i}" onclick="registrarSeparacao(${i}, 'em falta')">Em Falta</button>
              </div>
            </div>
          </div>
        `;
      });
    }

    function carregarFiltros() {
      const produtos = [...new Set(lista.map(i => i.produto))];
      const cores = [...new Set(lista.map(i => i.cor))];
      const estampas = [...new Set(lista.map(i => i.estampa))];

      produtos.forEach(p => {
        const opt = document.createElement('option');
        opt.value = p;
        opt.textContent = p;
        document.getElementById('filtroProduto').appendChild(opt);
      });
      cores.forEach(c => {
        const opt = document.createElement('option');
        opt.value = c;
        opt.textContent = c;
        document.getElementById('filtroCor').appendChild(opt);
      });
      estampas.forEach(e => {
        const opt = document.createElement('option');
        opt.value = e;
        opt.textContent = e;
        document.getElementById('filtroEstampa').appendChild(opt);
      });
    }

    document.getElementById('filtroProduto').onchange = aplicarFiltros;
    document.getElementById('filtroCor').onchange = aplicarFiltros;
    document.getElementById('filtroEstampa').onchange = aplicarFiltros;
    document.getElementById('filtroTamanho').onchange = aplicarFiltros;
    document.getElementById('filtroData').onchange = aplicarFiltros;

    carregarFiltros();
    aplicarFiltros();
  </script>
</body>
</html>


// 📦 backendPicking.gs | Módulo separado para Pick, Check e Pack - Berzerk x Orbitta

function doGet(e) {
  const painel = (e && e.parameter && e.parameter.painel) ? e.parameter.painel : "painelPicker";
  const template = HtmlService.createTemplateFromFile(painel);
  return template.evaluate().setTitle("Painel Picker - Berzerk").setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

// ===============================
// 🔁 registrarContagemRotineira
// ==============================
function registrarContagemRotineira(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");
  const abaBalanco = ss.getSheetByName("Log Balanço Blitz 5S") || ss.insertSheet("Log Balanço Blitz 5S");
  const abaDestino = ss.getSheetByName("entrada_destinacao_produto");
  const data = new Date();

  const cabecalho = [
    "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino", "OP", "Data Registro",
    "Qtd Entrada", "Qtd Saída", "Tipo Movimentação", "SKU", "Saldo", "Fonte", "Última ocorrência", "Classificação"
  ];

  if (abaLog.getLastRow() === 0) abaLog.appendRow(cabecalho);
  if (abaBalanco.getLastRow() === 0) abaBalanco.appendRow(cabecalho);

  dados.forEach(item => {
    const linha = [
      item.produto, item.cor, item.tamanho, item.estampa, item.responsavel,
      "CONTAGEM", item.destino || "-", "-", data,
      item.quantidade || 0, '', 'CONTAGEM ROTINEIRA', item.sku,
      item.quantidade || 0, 'WEBAPP', data, item.classificacao
    ];
    abaLog.appendRow(linha);
    abaBalanco.appendRow(linha);
  });

  if (abaDestino) {
    const ultimaCol = abaDestino.getLastColumn();
    const titulo = abaDestino.getRange(1, ultimaCol).getValue();
    if (titulo !== "Classificação do produto") abaDestino.getRange(1, ultimaCol + 1).setValue("Classificação do produto");
    dados.forEach(item => {
      abaDestino.appendRow([null, item.produto, item.cor, item.tamanho, item.estampa, item.responsavel, null, item.destino, 'Contagem Rotineira', item.quantidade, item.sku, item.classificacao]);
    });
  }
}


// =============================================
// 🚛 registrarRetiradaPickAndPacking (Pick/Check)
// =============================================
function registrarRetiradaPickAndPacking(dados) {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaLog = ss.getSheetByName("log_pickandpacking") || ss.insertSheet("log_pickandpacking");
  const abaResumo = ss.getSheetByName("resumo_separado") || ss.insertSheet("resumo_separado");
  const abaEstoque = ss.getSheetByName("Log Estoque Total") || ss.insertSheet("Log Estoque Total");
  const abaEstampadas = ss.getSheetByName("log_estampadas") || ss.insertSheet("log_estampadas");

  if (abaLog.getLastRow() === 0) abaLog.appendRow([
    "Data da movimentação", "Produto", "Cor", "Tamanho", "Estampa", "Responsável",
    "Tipo de Movimentação", "Classificação", "Quantidade", "Local", "Saldo"
  ]);

  if (abaResumo.getLastRow() === 0) abaResumo.appendRow([
    "Data", "Produto", "Cor", "Estampa", "Tamanho", "Quantidade", "Responsável"
  ]);

  if (abaEstoque.getLastRow() === 0) abaEstoque.appendRow([
    "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Origem", "Destino", "OP", "Data Registro",
    "Qtd Entrada", "Qtd Saída", "Tipo Movimentação", "SKU", "Saldo", "Fonte", "Última ocorrência"
  ]);

  if (abaEstampadas.getLastRow() === 0) abaEstampadas.appendRow([
    "Data", "Produto", "Cor", "Tamanho", "Estampa", "Responsável", "Tipo", "Quantidade", "SKU"
  ]);

  const dataStr = Utilities.formatDate(new Date(), "GMT-3", "yyyy-MM-dd HH:mm:ss");

  dados.forEach(item => {
    const sku = gerarSKU(item.produto, item.cor, item.tamanho);

    abaLog.appendRow([
      dataStr, item.produto, item.cor, item.tamanho, item.estampa, item.responsavel,
      "Pick and Packing - Retirada", item.classificacao, item.quantidade, item.local, item.saldo
    ]);

    abaResumo.appendRow([
      dataStr, item.produto, item.cor, item.estampa, item.tamanho, item.quantidade, item.responsavel
    ]);

    abaEstoque.appendRow([
  item.produto, item.cor, item.tamanho, item.estampa, item.responsavel,
  "Separação", "Expedição", "-", new Date(),
  "", item.quantidade, "SAÍDA - SEPARAÇÃO", sku,
  0, "WEBAPP", new Date(), item.classificacao
]);


    if (item.estampa && item.estampa.toLowerCase() !== 'lisa') {
  abaEstampadas.appendRow([
    new Date(), item.produto, item.cor, item.tamanho, item.estampa, item.responsavel,
    "SAÍDA - SEPARAÇÃO", item.quantidade, sku
  ]);
}

  });

  recalcularSaldosEstoque();
}

function gerarSKU(produto, cor, tamanho) {
  const normalizar = s => (s || '').normalize("NFD").replace(/[^A-Z0-9]/gi, "").toUpperCase();
  const p = normalizar(produto).replace(/[AEIOU]/gi, "").substring(0, 3);
  const c = normalizar(cor).replace(/[AEIOU]/gi, "").substring(0, 2);
  return `${p}${c}${tamanho}`;
}

// ✅ Link interno de navegação entre painéis
function abrirPainelPicker() {
  const url = 'https://script.google.com/macros/s/AKfycbwsciVuIiPSuvI5y7U4H9jObVL7zpyS_J8ojAZuOnvCRb2_tRU7kUkv7i8oPJR1BwzsGQ/exec?painel=painelPicker';
  const html = `<script>window.location.href = '${url}';</script>`;
  return HtmlService.createHtmlOutput(html);
}

function abrirPainelEstoque() {
  const url = 'https://script.google.com/macros/s/AKfycbzyUTD1-_FnIGx6ERicjjULDiHHDUhhGnH9SB7bSCA86fQDlhz_zk5_rsWjUZFHgbjgaA/exec?painel=painelEstoque';
  const html = `<script>window.location.href = '${url}';</script>`;
  return HtmlService.createHtmlOutput(html);
}

// ===============================================
// 🔗 Tiny API Integration - Pedidos e Casamento
// ===============================================

// 🔄 Sincroniza pedidos do Tiny (limitado por paginação leve)
function sincronizarPedidosTinyComPaginacao(token, limitePaginas = 1) {
  const pedidos = [];
  let pagina = 1;
  let totalPaginas = 1;

  do {
    const url = `https://api.tiny.com.br/api2/pedidos.pesquisa.php?token=${token}&formato=json&pagina=${pagina}`;
    const resposta = UrlFetchApp.fetch(url, { muteHttpExceptions: true });
    const json = JSON.parse(resposta.getContentText());

    if (json.retorno.status !== "OK") {
      Logger.log("❌ Erro na chamada da API do Tiny: " + JSON.stringify(json.retorno));
      break;
    }

    const pedidosPagina = json.retorno.pedidos || [];

    pedidosPagina.forEach(p => {
      const pedido = p.pedido;
      pedidos.push({
        numero: pedido.numero,
        nome: pedido.nome,
        situacao: pedido.situacao,
        data_pedido: pedido.data_pedido,
        codigo_rastreamento: pedido.codigo_rastreamento,
        numero_ecommerce: pedido.numero_ecommerce,
        valor: pedido.valor,
        data_prevista: pedido.data_prevista
      });
    });

    totalPaginas = Math.min(parseInt(json.retorno.numero_paginas) || 1, limitePaginas);
    pagina++;

  } while (pagina <= totalPaginas);

  Logger.log(`✅ ${pedidos.length} pedidos sincronizados (limite de ${limitePaginas} páginas).`);

  return pedidos;
}

// 📦 Obter itens detalhados de um pedido específico (necessário pro casamento por SKU)
function buscarDetalhesPedidoTiny(token, numeroPedido) {
  const url = `https://api.tiny.com.br/api2/pedido.obter.php?token=${token}&numero=${numeroPedido}&formato=json`;
  const resposta = UrlFetchApp.fetch(url, { muteHttpExceptions: true });
  const json = JSON.parse(resposta.getContentText());

  if (json.retorno.status !== "OK") {
    Logger.log(`❌ Erro ao buscar detalhes do pedido ${numeroPedido}`);
    return null;
  }

  return json.retorno.pedido.itens || [];
}

function getResumoSeparadoParaCasamento() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const abaResumo = ss.getSheetByName("resumo_separado");
  const dados = abaResumo.getDataRange().getValues();

  const cabecalho = dados[0];
  const linhas = dados.slice(1);

  const idxProduto = cabecalho.indexOf("Produto");
  const idxCor = cabecalho.indexOf("Cor");
  const idxEstampa = cabecalho.indexOf("Estampa");
  const idxTamanho = cabecalho.indexOf("Tamanho");
  const idxQuantidade = cabecalho.indexOf("Quantidade");

  return linhas.map(linha => ({
    produto: linha[idxProduto],
    cor: linha[idxCor],
    estampa: linha[idxEstampa],
    tamanho: linha[idxTamanho],
    quantidade: linha[idxQuantidade]
  })).filter(l => l.produto); // ignora linhas vazias
}


// 🤝 Casar itens separados com pedidos reais
function casarComPedidosTiny(token) {
  const pedidos = sincronizarPedidosTinyComPaginacao(token, 1); // só 1 página
  const separados = getResumoSeparadoParaCasamento();

  const casados = [];

  separados.forEach(sep => {
    for (let pedido of pedidos) {
      const match =
        pedido.nome?.toUpperCase().includes(sep.produto.toUpperCase()) &&
        pedido.nome?.toUpperCase().includes(sep.cor.toUpperCase()) &&
        pedido.nome?.toUpperCase().includes(sep.estampa.toUpperCase()) &&
        pedido.nome?.toUpperCase().includes(sep.tamanho.toUpperCase());

      if (match) {
        casados.push({
          numeroPedido: pedido.numero,
          cliente: pedido.nome,
          ...sep
        });
        break;
      }
    }
  });

  Logger.log(`✅ Casados encontrados: ${casados.length}`);
  return casados;
}

function testarCasamentoTiny() {
  const token = "1dcbf023e97edfae2eb504ca64e9a36c0050bdf22932d9261d19f06ed9b695b7";
  const casados = casarComPedidosTiny(token);
  Logger.log(casados.slice(0, 5));
}


e aí o grupo de csvs que são diversos

aba procv- nome colunas 	indice_coluna	exemplo 1	exemplo-2													
ID	A	705407304	706430933													
SKU	B	7893739905570	7891639879717													
DESCRIÇÃO	C	Bermuda Moletom - Verde Militar - G - Verde	Camisa Poliamida Tech - Branco - G													
Produto	D	Bermuda Moletom	Camisa Poliamida Tech													
URL IMAGEM 1	E															
Produto	F	Bermuda Moletom	Camisa Poliamida Tech													
Estampa	G	LISA	LISA													
TAMANHO	H	G	G													
COR	I	Verde	Branco													
																
aba validacao_suspensa	indice_coluna	exemplo 1	exemplo-2	exemplo-3	exemplo-4	exemplo-5										
Produto	A	OVERSIZED	POLIAMIDA TSHIRT	CAMISA DRYFIT	SHORTS COMPRESSÃO	RAGLAM										
Tecido Principal	B	COTTON	POLIAMIDA	DRYFIT	FAVO LIGHT	DRYFIT NACIONAL										
Tecido Complementar	C	VIÉS COTTON	POLIDRY(FORRO)	VIÉS POLIAMIDA	VIÉS DRYFIT	RIBANA 2P1										
AVIAMENTOS	D	VIÉS COTTON	VIÉS DRYFIT	VIÉS POLIAMIDA	VIÉS MODAL	ELÁSTICO E CORDÃO										
Cor	E	Preto	Azul Marinho	Canela 	Branco	PRETO REATIVO										
Malharia	F	XT	JMEI	RAFAEL	MARIANO	LUNELI										
Confecção	G	JAPONÊS	GUILHERMO	CASAL 20	IRAJA	MAELE										
Status do Tecido 	H	Enviado completo	Enviado Parcial	Aguardando envio	Atrasado											
Status corte	I	Concluído	Entregas futuras	Em corte	Atrasado											
Motorista	J	Zé	Gui	Barrabás	Jesus											
Status Confecção	K	CONCLUÍDO	TRANSPORTE	EM COSTURA	PARCIAL	Atrasado										
Status Pgto Confecção	L	Não pago	Pago													
Cortador	M	Antonio	Tião	Carlos Daniel	Interno	Julian										
Estampa	N	LegDay	EXCLUSIVA	Olympia	MITHY	ArmorofGod										
																
aba produto_consumo_custo	indice_coluna	exemplo-1														
Produto	A	OVERSIZED														
Tecido Principal	B	Cotton														
Rendimento por KG	C	3,3														
Consumo por PC	D	0,303														
Rolos por Corte	E	50														
Tecido complementar 1 e Aviamentos 	F	Viés de Cotton														
Rendimento por KG_complementar	G	225,0														
KG por PC_complementar	H	0,004														
Tecido_Aviamentos_2	I	Ribana 2P1														
Tecido Consumo 3	J	0,051														
Unidade de medida	K	Gramas														
Categoria	L	Top														
Grade Padrão	M	2P|3M|3G|2GG|1XG														
Gramatura padrão do Tecido Principal	N	200														
Insumos a Enviar	O	Etiqueta de Tamanho, Etiqueta de Composição,  Viés, Gola.														
Tecido	P	Cotton														
Tipo	Q	Tecido Principal														
Malharia	R	XT														
Malharia e Tecido	S	Cotton-XT														
Valor KG Tecido	T	R$ 49,00														
Col vazia	U															
Produto+Confecção	V	JAPONÊS-OVERSIZED														
Confecção	W	JAPONÊS														
Produto Confecção	X	OVERSIZED														
Custo Confecção	Y	R$ 5,00														
																
																
aba matriz_fornecimento	indice_coluna	exemplo-1														
Código do fornecedor	A	AT														
Produtos	B	Shorts de Compressão														
Fornecedor	C	Antonio														
Tipo	D	Confecção														
Custo	E	R$ 9,50														
Capacity_nom_mes	F	40000														
Capacity_semanal	G	10000														
WIP	H	0														
WIP %	I	0,00%														
Flag WIP	J	Fornecedor ocioso 🥱!														
Calendário Semanal 	K															
Lead Time	L	20														
Categoria	M	Bottom														
Endereço	N	Rua das Orquideas, 130														
Ordem de Rota (Partindo de Rua Suapé, 37)	O															
CNPJ	P															
E-mail	Q															
Telefone	R	11 94324-3493														
Contato	S															
Prazo de Pgto	T	45														
Capacity_real	U															
Fornecedor-Produto	V	Antonio-Shorts de Compressão														
																
																
aba criador_sku	indice_coluna	exemplo-1	exemplo-2													
cor_cadastrada	A	Vinho	Azul Marinho													
codigo_cor	B	VNH	AZM													
produto_cadastro	C	Camisa Dryfit	OVERSIZED													
codigo_produto	D	CDF	OVR													
estampa_cadastrada	E	Symbol	Lisa													
codigo_estampa		SYB	LSA													
																
aba skus_internos	indice_coluna	exemplo-1														
Produto	A	Camisa Dryfit														
Cor	B	Vinho														
Estampa	C	Symbol														
Tamanho	D	M														
codigo_produto	E	#N/A														
codigo_cor	F	VNH														
codigo_estampa	G	SYB														
sku_interno	H	#N/A														
																
																
aba log_corte	indice_coluna	exemplo-1	exemplo-2													
Data Registro	A	16/05/2025 16:46	13/05/2025 12:00													
Tipo de Acesso	B	Enfesto + Corte	Recebimento - Tecido													
Usuário	C	Dai	daiane1@berzerk.com.br													
Malharia	D	XT	XT													
Tecido	E	Cotton	Cotton													
Cor	F	Azul Marinho	Preto													
Produto	G	OVERSIZED	OVERSIZED													
Romaneio/NF	H	61212	61212													
Conformidade	I	conforme	Pendente													
Aferição de Pesagem/Gramatura	J	Sim	Pendente													
"Comprovante e Decisão- 5








































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































- Tipo 5"	K	✅ Enfesto + Corte registrado	Aguardando decisão													
Gramatura	L															
Aferição de Peso dos Rolos	M															
Rolos Total	N	45	50													
Numero de Partida	O															
ID Partida	P	802	116													
Rolos Partida	Q	45	50													
Comprovante e Decisão- Tipo 2	R															
OPS vinculadas	S	OP5CZL80278B-1/1-MT	OP5CPR11646A-1/2-NA1													
Num de Cortes Recomendado	T															
Arquivo Risco	U															
resumo de folhas e quantidades	V	"📦 Total Estimado: 2580 peças

P: 430
M: 860
G: 645
GG: 430
XG: 215"														
Junção de CorteOP	W															
Formulário decisão do usuário	X															
Responsável do Enfesto	Y	Dai														
Início do Enfesto	Z	2025-04-28 16:46														
Num de Rolos Enfestados	AA	45														
Se teve rolos bloqueados	AB	0														
Motivos	AC															
Calculo de Rolos	AD	45														
Número de Folhas	AE	215														
Fim do Enfesto	AF	2025-04-29 16:46														
Registro de finalização de enfesto	AG	16/05/2025 16:46														
Comprovante e Decisão- Tipo 3	AH	✂️ Corte conforme estimativa														
OPS em corte	AI	OP05CTZL3A-1/1														
Inicio Corte	AJ	2025-04-28 16:46														
Grade	AK	P430-M860-G645-GG430-XG215														
Quantidade de Tamanhos	AL	2580														
Folhas	AM	215	Aguardando Enfesto													
Retalhos?	AN	Não														
Quantidade Cortada	AO	2580														
Quantidade cortada por tamanho	AP	{"G":645,"M":860,"XG":215,"GG":430,"P":430}														
"Comprovante e Decisão- Tipo 4










































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































 Tipo "	AQ															
Check de Recebimento	AR															
folhas cortadas tamanho	AS															
log de mudança	AT															
"Comprovante e Decisão- 5










































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































- Tipo 5"	AU															
numero de volumes	AV															
resumo dos volumes	AX															
"Comprovante e Decisão-6











































































































































































































































































































































































































































































































































































































































































































































































































































































































































































- 6"	AW															
																
																
aba log_estampadas	indice_coluna	exemplo-1	exemplo-2	exemplo-3												
Data da movimentação	A	16/06/25	29/05/2025 18:32:08	19/06/2025 09:40:52												
Produto	B	Oversized	Camisa Dryfit	OVERSIZED												
Cor	C	Caqui	Preto	Preto												
Tamanho	D	P	GG	M												
Estampa	E	Mithy	Symbol	Donnut												
Responsavél	F	Dai		Cris												
Tipo de Movimentação	G	Balanço- Blitz 5S	ENTRADA - TRANSFORMAÇÃO	SAÍDA - SEPARAÇÃO												
Classificação	H	Site	Estampada	120												
Quantidade	I	28	30	VRSPRM												
Local	J	Montanaro	Pick And Packing													
Saldo	K	28	30													
																
																
aba log_estoque_total	indice_coluna	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED										
Produto	A	Preto	Preto	Preto	Preto	Preto										
Cor	B	P	P	P	P	P										
Tamanho	C	Lisa	Lisa	LegDay	Donnut	Lisa										
Estampa	D	Dai	Léo	Lucas	Dai	Léo										
Responsável	E	Balanço	Entrada - Pulmão	Saída - Estampar	Contagem Rotineira	-										
Origem	F	Pulmão-Montanaro	Pulmão-Montanaro	Máquina de Silk	Pulmão-Suapé	Pulmão-Montanaro										
Destino	G	-	-	-	-	-										
OP	H	28/05/2025	10/06/2025	11/06/2025	19/06/2025	24/06/2025										
Data	I	3.600	1.247		417	3.792										
Qtd Entrada	J			115												
Qtd Saída	K	BALANÇO	ENTRADA - PULMÃO	SAÍDA - ESTAMPAR	CONTAGEM ROTINEIRA	BALANÇO										
Tipo	L	OVRPRTLSAP	VRSPRP	VRSPRP	VRSPRP	OVE-PRE-P										
SKU	M	3.600				3.792										
Saldo	N	WEBAPP	WEBAPP	WEBAPP	WEBAPP	WEBAPP										
Origem Registro	O	✅				24/06/2025										
Ultima_ocorrencia	P															
SKU Transformado	Q	⚠️ SKU não encontrado para estampa: OVERSIZED||PRETO||P||LISA 🔄 Balanço redefiniu o saldo	⚠️ SKU não encontrado para estampa: OVERSIZED||PRETO||P||LISA	⚠️ SKU não encontrado para estampa: OVERSIZED||PRETO||P||LEGDAY	⚠️ SKU não encontrado para estampa: OVERSIZED||PRETO||P||DONNUT	⚠️ SKU não encontrado para estampa: OVERSIZED||PRETO||P||LISA 🔄 Balanço redefiniu o saldo										
Observação	R															
																
aba log_confecção	indice_coluna	exemplo-1	exemplo-2	exemplo-3												
Confecção Registro	A	Japonês	JAPONÊS	18/06/2025 14:46:09												
Data de Acesso	B	24/05/2025 11:24:39	24/05/2025 11:30:33	Painel Confecção												
OPs Alocadas	C	OP5CFL745EFF-1/1-JP	OP5CCS1838A1-1/1-JP	OP5CCS5488A1-1/1-MT												
Produto	D	OVERSIZED	OVERSIZED	OVERSIZED												
Cor	E	FLORESTA	CASTOR	CASTOR												
Data Prevista	F			Cotton												
PCs Estimadas	G															
Valor Prévio de Pgto	H															
Qtd Cortada P	I															
Qtd Cortada M	J															
Qtd Cortada G	K															
Qtd Cortada GG	L															
Qtd Cortada XG	M															
Total Cortado	N															
Final do Corte	O															
Prévia de Pgto	P															
NF- Remessa Industrialização	Q															
Data Real Entrega Confecção	R															
Agendamento de Envio	S															
Data de Envio	T															
Motorista	U	213	588													
Data de Início Confecção	V	647	0	Costura finalizada conforme												
Status Confecção	W	213	0	Costura finalizada conforme												
Qtd Costurada P	X	0	0													
Qtd Costurada M	Y	0	0	18/06/2025 14:46:09												
Qtd Costurada G	Z	1073	588													
Qtd Costurada GG	AA	2025-04-24	2025-04-24													
Qtd Costurada XG	AB			18/06/2025												
Total Costurado	AC															
Data finalização costura	AD															
Data de Agendamento Retirada Confecção	AE	2025-04-28	2025-04-28													
Data de Retirada Real Confecção	AF															
Valor a Pagar Confecção	AG															
Data de Vcto Confecção	AH															
NF- Retorno Industrializado	AI															
Motorista	AJ															
Status de recebimento confecção	AL	Entregue na confecção	Entregue na confecção													
Status de confecção	AM	Costura finalizada	Costura finalizada													
																
																
																
aba senhas_atuais	exemplo-1	exemplo-2	exemplo-3	exemplo-4	exemplo-5	exemplo-6	exemplo-7	exemplo-8	exemplo-9							
Nome	Antonio	Cris	Gu	Edna	Dai	Kado	Matheus	Jorginho	Mewtz							
Código	AT															
Senha Padrão	AntonioAT	CRIS1	GU1	EDNA1	DAI1	KADO1	MATHEUS1	JORGINHO1	CEO1							
Perfil	Confecções	Pick and Packing, Qualidade, Estoque 	Pick and Packing, Estoque	Silkscreen	Administrador	Entrada de Tecido, Alocação, Recebimento de Tecido, Corte, Criação de User e Senha	Administrador leve, acesso a todos os painéis, sem mexer em API e outros.	Administrador leve, acesso a todos os painéis, sem mexer em API e outros.	Administrador leve, acesso a todos os painéis, sem mexer em API e outros.							
																
																
aba entradas no pulmão	indice_coluna	exemplo-1	exemplo-2	exemplo-3												
Data	A	2025-06-03	12/06/2025	24/06/2025												
Responsável	B	OVERSIZED	OVERSIZED	OVERSIZED												
Produto	C	Azul Marinho	CASTOR	caqui/canela												
Cor	D	G	P	XG												
Confecção	E	Lisa	Lisa	Lisa												
Tamanho P	F	Léo	Léo	Léo												
Tamanho M	G	JAPONÊS	MATHEUS	-												
Tamanho G	H	Pulmão-Montanaro	Pulmão-Montanaro	Pulmão-Montanaro												
Tamanho GG	I	Entrada - Pulmão	Entrada - Pulmão	Entrada - Pulmão												
Tamanho XG	J	2222	394	464												
Total Estimado	K	VRSZLG	VRSCSP	OVECAXGLS1												
																
aba entrada_destinacao_tecido	indice_coluna	exemplo-1	exemplo-2	exemplo-3	exemplo-4	exemplo-5	exemplo-6	exemplo-7								
Data Registro	A	14/05/2025 10:02:10	17/05/2025 18:43:00	17/05/2025 18:43:00	17/05/2025 18:43:00	17/05/2025 18:43:00	17/05/2025 18:43:00	17/05/2025 18:43:00		18/06/2025 18:08:06	18/06/2025 18:08:06					
ID Entrada	B	ENTRADA-054648A1	ENTRADA-054648A1	ENTRADA-054648A1	ENTRADA-054648A1	ENTRADA-054648A1	ENTRADA-054648A1	ENTRADA-054648A1		ENTRADA-F4FDF004	ENTRADA-F4FDF004					
Tipo Linha	C	Mãe	Detalhe	Detalhe	Detalhe	Detalhe	Detalhe	Detalhe		Mãe	Detalhe					
Tipo Entrada	D	Programada	Programada	Programada	Programada	Programada	Programada	Programada		Programada	Programada					
Produto	E	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED	OVERSIZED		OVERSIZED	OVERSIZED					
Malharia	F	XT	XT	XT	XT	XT	XT	XT		XT	XT					
Cor	G	CASTOR	CASTOR	CASTOR	CASTOR	CASTOR	CASTOR	CASTOR		Branco	Branco					
Tecido	H	Cotton	Cotton	Cotton	Cotton	Cotton	Cotton	Cotton		Cotton	Cotton					
Romaneio	I	65144	65144	65144	65144	65144	65144	65144		61212	61212					
Data Envio	J	06/05/2025	06/05/2025	06/05/2025	06/05/2025	06/05/2025	06/05/2025	06/05/2025		09/04/2025	09/04/2025					
Responsável	K	Dai	Dai	Dai	Dai	Dai	Dai	Dai		daiane1@berzerk.com.br	daiane1@berzerk.com.br					
KG Principal	L	2518	962	962	370	832,5	166,5	333		1248	666					
Rolos Principal	M	144	52	52	20	45	9	18		69	36					
KG Complementar	N	33	0	0	0	0	0	0		16	0					
Rolos Complementar	O	0	0	0	0	0	0	0		1	0					
KG Aviamento	P	134	0	0	0	0	0	0		98	0					
Rolos Aviamento	Q	0	0	0	0	0	0	0		7	0					
KG Ribana	R	0	0	0	0	0	0	0		0	0					
Rolos Ribana	S	0	0	0	0	0	0	0		0	0					
PCS Estimadas	T	8309	3174	3174	1220	2747	549	1098		4118	2197					
Total KG	U	2685	962	962	370	832,5	166,5	333		1362	666					
Total Rolos	V	144	52	52	20	45	9	18		77	36					
Valor Total s/ Viés	W	123382	47138	47138	18130	40792,5	8158,5	16317		61152	32634					
KG Viés	X	33,24								16,47						
Rolos Viés	Y	2								1						
Valor Viés	Z	2908,15								1441,3						
Valor Final	AA	126290,15	48249,05651	48249,05651	18557,32943	41753,99121	8350,798243	16701,59649		62593,3	33403,15529					
Data Vencimento	AB	24/05/2025	24/05/2025	24/05/2025	24/05/2025	24/05/2025	24/05/2025	24/05/2025		17/05/2025	17/05/2025					
Status Ribana	AC	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg	⚠️ Ribana Insuficiente - Solicitar mais 125.90 kg		⚠️ Ribana Insuficiente - Solicitar mais 62.40 kg	⚠️ Ribana Insuficiente - Solicitar mais 62.40 kg					
Cortador	AD	Interno	Interno	Interno	Interno	✔️OP5CCS5488A1-1/1-MT	Interno	Interno		Interno	Interno					
OP	AE		OP5CCS1828A1-1/2-C20	OP5CCS1828A1-2/2-GL	OP5CCS1838A1-1/1-JP	OP5CCS5488A1-1/1-MT	OP5CCS5508A1-1/1-MC	OP5CCS1858A1-1/1-AL			OP5CBR770004-1/1-GL					
Confecção	AF		CASAL 20	GUILHERMO	JAPONÊS	MATHEUS	MAELE	ART LIVRE			Guilhermo					
ID Partida	AG		182	182	183	548	550	185			770					
Corte #	AH		1	2	1	1	1	1			1					
Total Cortes	AI		2	2	1	1	1	1			1					
Status Recebimento Tecido	AJ	Recebido no corte	Recebido no corte	Recebido no corte	Recebido no corte	Recebido no corte	Recebido no corte	Recebido no corte		Recebido no corte	Recebido no corte					
Status Corte	AL		Tecido Recebido	Tecido Recebido	Tecido Recebido	Tecido Recebido	Tecido Recebido	Tecido Recebido			Tecido Recebido					
Entrega Confecção	AM				Recebido na Confecção											
Retorno confecção	AN		 		Costura finalizada	Costura finalizada										
Entrega Bzk	AO															
aba mapaSKU	indice_coluna	exemplo-1	exemplo-2	exemplo-3												
SKU	A	CDFVNHLSAP	CDFVNHLSAGG	CDFPRTLSAP	CDFPRTLSAM											
Produto	B	CAMISETA DRYFIT	CAMISETA DRYFIT	CAMISETA DRYFIT	CAMISETA DRYFIT											
Cor	C	VINHO	VINHO	PRETO	PRETO											
Tamanho	D	P	GG	P	M											
Estampa	E	LISA	LISA	LISA	LISA											
Saldo Lisa	F	411	651	522	1988											
Saldo Estampa	G	0	0	0	0											
Último Cálculo	H	02/07/2025, 17:37:04	02/07/2025, 17:37:04	02/07/2025, 17:37:04	02/07/2025, 17:37:04											
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																
																

