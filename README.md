# Mortalidade Infantil no Acre e Seus Condicionantes (2022)
### Análise Espacial e Estatística da Mortalidade Infantil no Acre, Recorte por município - Acre (2022). Uma análise espacial das condições socioeconômicas e do acesso a serviços públicos.
![capa](capa.png)
---

## 1. Contextualização e Objetivo
* A investigação da mortalidade infantil no Acre evidencia a dimensão crítica dos determinantes sociais e territoriais da saúde no Brasil. De acordo com o relatório Cenário da Infância e Adolescência no Brasil (Fundação Abrinq, 2026), a Região Norte liderou a taxa de mortalidade infantil em 2024, registrando 15,7 óbitos por mil nascidos vivos, em contraste com a Região Sul, que apresentou o menor indicador do país (10,4 por mil). Diante dessa expressiva disparidade macrorregional, o estado do Acre configura-se como um recorte geográfico estratégico para analisar as correlações e os condicionantes socioespaciais que atuam como agravantes ou fatores de proteção à sobrevida infantil na Amazônia.
* Foram utilizados oito indicadores, construídos a partir de bases públicas do IBGE, do DATASUS e do Ministério da Saúde, integrados em ambiente de Sistema de Informação Geográfica. A análise empregou o coeficiente de correlação de Pearson e a produção de mapas temáticos coropléticos bivariados, cruzando a mortalidade infantil com PIB per capita, acessibilidade geográfica, escolaridade materna e cobertura de pré-natal.
* Para a realização desse projeto utilizei o QGIS para o mapeamento e análises de SIG e PostgreSQL, além do Excel para correções no banco de dados. O plugin utilizado para a geração da legenda bivariada dos mapas foi o "Bivariate legend".
* O presente estudo foi desenvolvido como Projeto Final da disciplina de Sistemas de Informação Geográfica do curso de Pós-graduação em Análise Ambiental e Gestão do Território (ENCE/IBGE), apresentado em formato de monografia. Além disso, o trabalho está em fase final de elaboração para submissão em formato de artigo científico.
* Esse trabalho foi feito em conjunto com o Gabriel Silva (@), colega de classe da pós-graduação da ENCE/IBGE, responsável pelas correlações de Pearson, análise de dados em fontes oficiais e confecção do slide/monografia, enquanto a minha pessoa ficou responsável pela confecção e correção do banco de dados (Excel e SQL), além da síntese dos indicadores e cartografia no QGIS.
---

## 2. Área de Estudo e Indicadores Selecionados
![Indicadores](RecortIndicadores.jpg)

* Recorte Espacial: Munícipios do Estado do Acre.
* Ano de Referência: 2022
* A seleção dos indicadores não foi arbitrária nem determinada exclusivamente pela disponibilidade de dados. Ela se apoia no referencial dos Determinantes Sociais da Saúde (DSS), definidos pela Comissão Nacional sobre os Determinantes Sociais da Saúde (CNDSS) como os fatores sociais, econômicos, culturais, étnicos e raciais, psicológicos e comportamentais que influenciam a ocorrência de problemas de saúde e seus fatores de risco na população (BUSS; PELLEGRINI FILHO, 2007).
* Esse arcabouço orienta diretamente a escolha dos oito indicadores aqui empregados. Revisões da literatura brasileira sobre mortalidade infantil, ao organizarem as variáveis significativamente associadas ao desfecho segundo as camadas do modelo de DSS, identificam de forma consistente a assistência pré-natal e a escolaridade materna na camada de condições de vida e trabalho, e o saneamento básico e a renda na camada de condições socioeconômicas e ambientais gerais.
* Os indicadores utilizados foram:
  - **Coeficiente de Mortalidade Infantil (CMI):** (Óbitos de menores de 1 ano ÷ Nascidos vivos) × 1.000, por residência; Fonte: DATASUS: SIM e SINASC (2022).
  - **PIB per Capita Municipal:** Cobertura de água por rede geral - PIB total do município ÷ população residente; Fonte: IBGE/SIDRA, Censo 2022.
  - **Cobertura de Esgotamento Sanitário Adequado:** % de domicílios com ligação à rede geral de distribuição, utilizada como forma principal; Fonte: Censo IBGE 2022.
  - **Cobertura Potencial da APS:** (Nº de equipes × parâmetro populacional por equipe) ÷ população do município × 100; Fonte: e-Gestor Atenção Básica (dez/2022).
  - **Escolaridade Materna:** (Nº de mães na faixa de escolaridade ÷ Total de mães) × 100; Fonte: DATASUS/SINASC (2022).
  - **Cobertura de Pré-Natal:** (Nº de mães na faixa de consultas ÷ Total de mães com pré-natal registrado) × 100; Fonte: DATASUS/SINASC (2022).
  - **Distância e Classificação de Acessibilidade Geográfica:** Cálculo do custo de deslocamento em minutos pela rede multimodal (rodoviária, fluvial e aérea) até o centro urbano de referência mais próximo na hierarquia REGIC; Fonte: IBGE, Índice de Acessibilidade Geográfica (2018), 'refinado pela equipe'.
---

## 3. Análises Estatísticas
![Estatísticas](correlacoes.jpg)

* Para responder à pergunta de pesquisa, foi calculado o coeficiente de correlação de Pearson (r) entre pares de variáveis, acompanhado do respectivo p-valor, adotando-se o nível de significância de 5% **(p < 0,05)**. O coeficiente de correlação de Pearson consiste em uma medida estatística que indica a força e a direção da relação linear entre duas variáveis quantitativas, representada pelo valor de **r**, que varia de -1 a 1, sendo:
  - **Correlação Positiva (r > 0):** As duas variáveis aumentam justas.
  - **Correlação Negativa (r < 0):** Quando uma variável aumenta, a outra diminui.
  - **Zero ( r = 0):** Não existe relação linear entre as variáveis.
  - **Intensidade:** Quanto mais próximo do 1 ou -1, mais forte é a associação.
    
* Este trabalho identificou que a cobertura de pré-natal adequada e a escolaridade materna, incorporadas ao estudo em sua fase final, apresentam associação significativa e mais robusta com a mortalidade infantil do que a capacidade econômica municipal isoladamente. A cobertura de pré-natal adequada, em particular, constitui o segundo achado mais forte de todo o estudo (r = -0,65; p = 0,001), superado apenas pela associação
entre distância e PIB per capita.
* Um achado adicional merece destaque: o isolamento geográfico, que explica fortemente a capacidade econômica municipal, não explica de forma robusta o acesso à assistência pré-natal (r = -0,11; p = 0,619) nem, de forma conclusiva, a escolaridade materna (r = -0,42; p = 0,050, no limiar da significância). Isso sugere que o acesso à assistência materna no Acre responde a determinantes distintos da simples distância geográfica, possivelmente relacionados à organização e à gestão local dos serviços de saúde.
---

## 4. Bancos de Dados e Análise Espacial

* A organização do banco de dados seguiu quatro etapas:
  - Padronização e tratamento dos dados tabulares;
  - Integração com a base geoespacial municipal;
  - Definição do método de classificação e da simbologia cartográfica;
  - Análise estatística de correlação entre os indicadores.

* Para a análise espacial conjunta dos determinantes de saúde, foram elaborados mapas coropléticos bivariados cruzando a taxa de mortalidade infantil com cinco covariáveis do estudo: PIB per capita, cobertura potencial da Atenção Primária à Saúde, acessibilidade geográfica, escolaridade materna e cobertura de pré-natal. Nessa etapa, cada indicador foi dividido em tercis — baixo, médio e alto —, formando uma legenda em matriz com nove classes de cores (3×3). Portanto, o método utilizado nos mapas bivariados é o dos tercis.
* As tabelas foram consolidadas em uma planilha-mestre única, utilizando o código do município como chave de junção comum a todas as fontes. O resultado é uma tabela de atributos com 22 linhas e uma coluna por indicador, importada e tratada diretamente no QGIS. Por trabalhar com dados brutos, muitas informações estavam em números absolutos, e para evitar erros, diversas correções precisaram ser feita no banco de dados utilizando a Calculadora de Campo nativa do QGIS, em ambiente SQL, para realizar a correção, síntese e a organização dos dados para a confecção dos indicadores e posterior síntese dos mapas. 
* A planilha-mestre foi unida à malha municipal oficial do IBGE para o estado do Acre por meio de junção do código do município, permitindo a espacialização de cada indicador. Os produtos cartográficos foram elaborados na Projeção Universal Transversa de Mercator (UTM), Datum SIRGAS2000, Fuso 19 Sul.
  - A tabela de atributos está disponível em: [tabela.csv](Tabela de atributos AC(2022).csv)
  - O dicionário de dados

---

## 5. Mapas Coropléticos Bivariados:
