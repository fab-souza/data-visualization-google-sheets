# data-visualization-google-sheets

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/data-visualization-google-sheets)

| :placard: Vitrine.Dev |    |
| -------------  | --- |
| :sparkles: Nome        | **data-visualization-google-sheets**
| :label: Tecnologias | Google Sheets
| :rocket: URL         | 
| :fire: Desafio     | Conteúdo do [curso](https://www.alura.com.br/curso-online-data-visualization-visualizacao-google-sheets)

![](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/90d87d11-28a1-41ab-91fa-3c5e64a34e01#vitrinedev)

# Sobre o curso 📚

Depois de aprender a explorar os dados e a fazer alguns modelos de regressão linear, a formação foi direcionada para a visualização de dados. Mostrando ferramentas para melhorar a apresentação dos resultados obtidos, dando ênfase em comunicação assertiva e a estruturar apresentações seguindo boas práticas, além de apresentar bibliotecas destinadas à criação de gráficos.

Neste repositório vou apresentar o que aprendi no curso **Data Visualization: técnicas de visualização com Google Sheets**, da formação [Data Science](https://www.alura.com.br/formacao-data-science), oferecido pela [Alura](https://www.alura.com.br/). O curso foi ministrado pelo [Daniel Siqueira](https://www.linkedin.com/in/daniel-siqueira-alura/) e aprendi:

- sobre os principais conceitos de visualização de dados e storytelling; 
- a como utilizar as cores e seguir os princípios de Gestalt; 
- a melhorar a visualização das tabelas, gráfico de colunas e de barras; 
- como acrescentar *séries* nos gráficos; 
- e a utilizar o gráfico de pizza de forma correta. 

Durante o curso, acompanhamos a jornada da Ana para elaborar um relatório destinado aos investidores e investidoras da empresa (fictícia) **Alura Market**, utilizando dados de diversos setores para responder questões específicas e potencializar a apresentação.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/8684448b-be86-48cf-85d5-546085d720a5)

# Minha prática 👩🏻‍💻

Para praticar o que aprendi, utilizei um dataset disponibilizado pelo [SIGA - Sistema de Informações de Geração da ANEEL] (https://dadosabertos.aneel.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel) referente ao parque gerador nacional, de diversas fontes de combustível e em diferentes fases: 
- outorga;
- construção não iniciada;
- em construção;
- em operação.

Em 2022, fiz um projeto particular analisando o setor energético nacional, usando este dataset em conjunto com outros, para comparar a geração nacional de energia elétrica, proveniente de fontes renováveis, com outros países. 

Caso tenha curiosidade, segue o link do [GitHub](https://github.com/fab-souza/meu-projeto-energia).

Para este projeto, pensei em fazer algo semelhante. Por se tratar de um dataset extenso, composto por mais do que quinze mil linhas, não usei outros datasets para responder às seguintes questões:

- Dentre os tipos de outorga, qual delas mais aparece?
- Quais são os estados com o maior número de empreendimentos (termo usado para referir-se às usinas geradoras de energia elétrica)?
- Dentre os tipos de empreendimentos registrados, em qual fase eles se encontram?
- Como está o incentivo à construção de novos empreendimentos? A cada ano, este número cresce de forma constante?
- Como está dividida a geração do parque gerador nacional?

---

Antes de começar a análise dos dados, acho melhor explicar o que é outorga e qual a diferença entre seus tipos. Segundo o [Dicionário Priberam](https://dicionario.priberam.org/outorga), outorga possui dois significados:

1. Ato ou efeito de outorgar.
2. Concessão; aprovação.

Um exemplo do uso deste termo, é quando recorremos ao serviço prestado por um(a) advogado(a). Ao assinar uma permissão para este profissional tomar uma decisão em seu nome, você está fazendo uma *outorga*. 

Quando se trata de geração de energia elétrica, em território nacional, existem três tipos de outorga:

- Autorização;
- Concessão;
- e Registro.

Essa diferença ocorre, porque dependendo da fonte de combustível e potência instalada, existe uma Lei específica para aquele tipo de empreendimento e sob qual outorga ele deve operar. No site do [Ministério de Minas e Energia](https://www.gov.br/aneel/pt-br/assuntos/geracao/outorgas) há uma explicação mais detalhada de como a classificação de outorga é feita. Caso tenha curiosidade, é só clicar no link.

Segundo o site [Jusbrasil](https://www.jusbrasil.com.br/noticias/diferenca-entre-autorizacao-permissao-e-concessao/334798287), uma outorga de Autorização “*É um ato administrativo por meio do qual a administração pública possibilita ao particular a realização de alguma atividade de predominante interesse deste, ou a utilização de um bem público*”, enquanto uma outorga de Concessão “*É o contrato entre a Administração Pública e uma empresa particular, pelo qual o governo transfere ao segundo a execução de um serviço público, para que este o exerça em seu próprio nome e por sua conta e risco, mediante tarifa paga pelo usuário, em regime de monopólio ou não*”. Já a outorga de Registro *é quando um empreendimento de geração de energia recebe o direito legal de operar*, nesta página da [ANEEL](https://www.gov.br/aneel/pt-br/centrais-de-conteudos/manuais-modelos-e-instrucoes/geracao/registro-autorizacao-e-concessao-de-empreendimentos-de-geracao/registro-de-rcg) é explicado como registrar empreendimento de geração de energia elétrica com potência instalada igual ou inferior a 5.000 kW.

Dito isso, para analisar as outorgas, criei uma nova página no Google Sheets e colei a coluna referente aos tipos de outorga. Para ter certeza que há somente os três tipos, fiz um *=UNIQUE* na coluna seguinte e seu retorno confirmou a existência dos três. Na coluna seguinte, fiz um *=CONT.SE* para me mostrar quantas vezes cada tipo apareceu na primeira coluna. Para ilustrar a diferença entre os valores, fiz um gráfico de barras. Porém, não achei interessante apresentar a diferença de valores desta forma. Por se tratar de um valor muito alto, em comparação aos demais, achei melhor apresentar esta informação em um cartão.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/b0baeb0f-0ddc-453b-865e-18f13ad7aa09)

---

Para responder a segunda pergunta, fiz algo semelhante. Criei uma nova página, colei apenas a informação referente a pergunta, fiz o *=UNIQUE*, fiz o *=CONT.SE* e plotei um gráfico de barras. A diferença entre o primeiro com os demais é bem grande, por isso achei melhor plotar um gráfico somente com os cinco estados com maior número de empreendimentos.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/e00f821f-df2c-4ebb-8473-b3c8a1c71b0c)

---

Seguindo para a próxima pergunta, desta vez, copiei duas colunas, a do *tipo de geração* e *em qual fase se encontram*. Fiz um *=UNIQUE* da coluna *tipo de geração* e obtive o seguinte retorno:

- PCH = Pequena Central Hidrelétrica
- UHE = Usina Hidrelétrica
- CGH = Central Geradora Hidrelétrica
- UTE = Usina Termelétrica
- UTN = Usina Termonuclear
- EOL = Central Geradora Eólica
- UFV = Central Geradora Solar Fotovoltaica
- CGU = Central Geradora Undi-elétrica

Para fazer a contagem de quantos empreendimentos estão em cada fase, criei uma tabela. Utilizei o retorno do *=UNIQUE* como índice, as *fases* ocuparam as colunas e a preenchi com um *=CONT.SES*. Com a tabela pronta, plotei um gráfico de barras empilhadas e fiz ajustes nas cores das barras. Usei tons de azul, porque no livro da Cole Nussbaumer, [Storytelling com Dados](https://www.amazon.com.br/Storytelling-com-Dados-Visualiza%C3%A7%C3%A3o-Profissionais/dp/8550804681/ref=asc_df_8550804681/?tag=googleshopp00-20&linkCode=df0&hvadid=379805395634&hvpos=&hvnetw=g&hvrand=10415295316985288941&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9101997&hvtargid=pla-812777209198&psc=1), ela escreve que usa tons de azul em suas apresentações para facilitar a compreenção da plateia/ouvintes, evitar que eles se distraiam e como uma forma de acessibilidade, já pode haver pessoas com daltonismo assistindo a apresentação.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/57b673e7-8deb-47a7-87c0-be4f227dbb8a)

---

A próxima pergunta foi respondida depois de alguns *malabarismos*... 😅 Depois de fazer o básico, criar uma nova página e colar as colunas necessárias, apliquei um filtro na coluna das *fases*, para que tivesse apenas as usinas que já estão *operando*. Na coluna **C**, usei um *=IFS* para retornar apenas o *ano* da data em que as usinas entraram em operação. Em outra coluna, usei um *=SORT* para colocar os anos em ordem crescente. Nas colunas seguintes, primeiro fiz um *=UNIQUE* e depois fiz um *=CONT.SE* para obter quantas vezes cada ano apareceu. Terminei com a criação do gráfico de linha, em que observamos que desde 2017, com exceção de 2019 e 2020, houve um crescimento no número de usinas que entraram em operação.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/73a9e8c3-20d3-4926-bfa6-b75d05864a3a)

---

Para a última pergunta, criei outra página, colei as colunas relevantes para respondê-la e criei um gráfico de pizza referente a frequência da *origem de combustível*. Nele, vemos que 61,7% das usinas (até metade de 2022) utilizam a energia solar para gerar energia elétrica.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/886a5769-730f-4595-9d2c-395b6fe8b51b)

Esta informação pode parecer um pouco estranha, já que em qualquer livro, ou matéria jornalística, vemos que a maior parte da energia elétrica gerada no Brasil é proveniente de hidrelétricas.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/88a7d9eb-1d92-41a0-8a90-1d2a320d7170)

E eles não estão errados. 

Ao plotar um novo gráfico, desta vez, somando a potência de cada *tipo de combustível*, vemos que 65,0% do total é proveniente de fonte hídrica.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/c4145f0c-9e49-4801-814d-c4bdcdd03f80)

---

Para finalizar, criei uma nova página para unir todas as análises.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/4c0ed343-fb12-4eb4-a549-2b9301adfa37)

# Conclusão 🏁

Ao concluir este projeto, vejo que as análises obtidas na 1ª, 4ª e 5ª pergunta, no meu ponto de vista, estão interligadas. Pois, 

1º: a outorga que mais apareceu é do tipo *Registro*. Lembrando que este é o tipo de regulamentação usado para empreendimentos de potência instalada igual ou inferior a 5.000 kW. Ou seja, sabe aquele sistema fotovoltaico que muita gente instalou nas casas, comércio e indústrias nos últimos anos? Se ele for igual ou inferior a 5.000 kW, sua outorga será do tipo *Registro*.

2º: a crescente no número de usinas que entraram em operação desde 2017, atribuo à [Resolução Normativa ANEEL nº 482/2012](http://www2.aneel.gov.br/cedoc/ren2012482.pdf), que permitiu que o consumidor brasileiro pode gerar sua própria energia elétrica a partir de fontes renováveis ou cogeração qualificada. (Fonte: [Agência Nacional de Energia Elétrica](https://www.gov.br/aneel/pt-br/assuntos/geracao-distribuida))

3º: no gráfico, vemos que 61,7% (9.540) das usinas são de origem *Solar*. Diante desta informação, em conjunto com as duas anteriores, posso inferir que a mudança na Lei, em conjunto com incentivos fiscais, criou a demanda pela aquisição de sistemas fotovoltaicos. Que posteriormente, geraram o *boom* no número de usinas que entraram em operação nos últimos anos. 

Em relação à segunda pergunta, eu não consegui inferir nenhuma hipótese relevante que justificasse a enorme diferença que há entre o número de usinas presentes no Pará, em relação aos demais. O estado também não possui boas condições de incidência solar ao longo do ano, algo que poderia justificar o número de usinas no local. 

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/eedcfc0e-552c-41a9-9829-6fc8a9c5ccca)

Mas, independente desta condição, isso não impede a instalação de novos sistemas fotovoltaicos. E estou me referindo somente a este tipo de usina, porque sua instalação é mais rápida, quando comparada com uma usina hidrelétrica, por exemplo. 

Já em relação à 3ª pergunta, o ponto que mais me chamou a atenção é que, apesar das mais de 3000 termelétricas em operação, ainda havia 56 em construção e mais 61 que não tiveram suas obras iniciadas…

![respira-fundo-deep-breath](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/e0973467-75a1-46af-977c-f8dd34928590)

No momento que estou escrevendo esta conclusão, o Brasil está passando por uma *onda de calor* no final do inverno e nem chegamos na primavera ainda. A previsão para a minha região é atingir 41° C nos próximos dias, algo que só acontece durante o verão.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/93c4cce4-4bce-47e8-bd29-357cfc6a2f68)

Voltando a análise. 

Sei que a construção deste tipo de usina é mais rápida, quando comparado aos demais. Ver que ele ainda recebe incentivo, apesar de todos os estudos que comprovam a associação entre a queima de combustíveis fósseis com o aquecimento global (Fonte: [WWF](https://www.wwf.org.br/nossosconteudos/educacaoambiental/conceitos/efeitoestufa_e_mudancasclimaticas/)) me deixou chateada, para não dizer outra coisa… Mas ao verificar o dataset original, vi algo que me deixou mais tranquila. Usinas que funcionam a base de biomassa também são classificadas como UTE, então para ter certeza que as usinas que ainda não entraram em operação terão a biomassa como combustível, seria preciso fazer uma análise diferente.

![image](https://github.com/fab-souza/data-visualization-google-sheets/assets/67301805/0d4cf299-840a-470c-90ea-d761e890958f)

Seguindo neste otimismo, o país tem 821 centrais eólicas, com mais 210 que não tiveram sua construção iniciada e mais 156 em construção. Já sobre as geradoras fotovoltaicas, até metade de 2022, o Brasil tinha 8.592 centrais operando, com mais 106 em construção e 842 que ainda estavam no papel. 

Em resumo, o país está caminhando rumo a uma ampliação na diversificação da matriz energética, algo que pode diminuir a dependência de energia elétrica proveniente da fonte hídrica.

---

Muito obrigada por chegar até aqui e até a próxima 🤗

## Ferramentas utilizadas 🧰

<p>
  <a href="https://www.google.com/sheets/about/" target="_blank" rel="noreferrer"> <img src="https://e7.pngegg.com/pngimages/301/1/png-clipart-google-sheets-logo-thumbnail.png" alt="google-sheets" width="40" height="40"/> </a>
</p>
