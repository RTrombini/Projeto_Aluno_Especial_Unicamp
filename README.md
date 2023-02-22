# Projeto Aluno Especial Unicamp


# Título do Projeto

O projeto proposto para a seleção dos alunos especiais para a disciplina "Deep Learning aplicado a sistemas de buscas" foi o de um sistema de Information Retrieval utilizando o algoritmo BM25.


Em paralelo, um segundo objetivo do projeto era a familiarização com a ferramenta ChatGPT da OpenAI para auxiliar no desenvolvimento da tarefa.

Um dos requisitos do projeto era a utilização da coleção CISI para testes de sistemas de IR, no endereço http://ir.dcs.gla.ac.uk/resources/test_collections/cisi/.

O algoritmo proposto segue a seguinte ordem:

    - Baixa a coleção da web;
    - Indexa toda a coleção;
    - Recebe uma entrada do usuário e filtra as palavras-chave dessa entrada;
    - Realiza uma busca nos arquivos indexados pelos resultados que melhor batem com as palavras-chave entradas, utilizando o algoritmo BM25.

# Indice:

    - Information Retrieval
    - Algortimo BM25
    - Coleção CISI
    - Biblioteca Whoosh
    - Implementação
    - Exemplos
    - Auxilio ChatGPT

# Information Retrieval

Um sistema de Information Retrieval (Recuperação de Informação) é um conjunto de técnicas, algoritmos e ferramentas que permitem a recuperação de informações relevantes a partir de um conjunto de dados não estruturados ou semi-estruturados, como textos, imagens ou sons. O objetivo principal desse sistema é permitir que o usuário encontre informações específicas em um grande conjunto de dados de maneira eficiente e eficaz.

Os sistemas de Information Retrieval geralmente incluem uma interface de usuário que permite ao usuário especificar suas consultas e receber os resultados relevantes. Além disso, esses sistemas podem incluir algoritmos de indexação, classificação e filtragem de dados, bem como técnicas de processamento de linguagem natural e aprendizado de máquina para melhorar a relevância e precisão dos resultados.

Os sistemas de Information Retrieval são amplamente utilizados em uma variedade de aplicações, como motores de busca da Web, bibliotecas digitais, sistemas de gerenciamento de documentos e sistemas de recomendação.

# Algortimo BM25

O algoritmo BM25 (Best Matching 25) é um algoritmo de pontuação de relevância amplamente utilizado em sistemas de recuperação de informação, como motores de busca na Web. É uma melhoria em relação ao algoritmo clássico de TF-IDF (Frequência de Termos-Inverso de Frequência de Documentos), que é amplamente utilizado em sistemas de recuperação de informação.

O BM25 considera o contexto da consulta do usuário e leva em consideração a frequência dos termos da consulta nos documentos, bem como a frequência dos termos nos documentos da coleção em geral. O algoritmo também leva em consideração a similaridade de comprimento entre o documento e a consulta, o que é importante porque documentos mais longos podem conter mais termos relevantes.

O algoritmo BM25 é baseado em três parâmetros ajustáveis, que são a frequência de termos nos documentos, a frequência de termos nos documentos da coleção e a média do comprimento dos documentos na coleção. Esses parâmetros podem ser ajustados para atender às necessidades específicas de um sistema de recuperação de informações.

O algoritmo BM25 é considerado um dos melhores algoritmos de pontuação de relevância para sistemas de recuperação de informações, porque é capaz de lidar com uma ampla variedade de consultas e documentos de forma eficiente e eficaz. Ele é amplamente utilizado em sistemas de busca na Web, sistemas de recomendação, sistemas de gerenciamento de documentos e outros sistemas de recuperação de informações.

# Coleção CISI

A Coleção CISI é uma coleção de documentos amplamente utilizada na área de recuperação de informações. Ela foi criada pela Commonwealth Scientific and Industrial Research Organisation (CSIRO) em colaboração com a Cranfield University na década de 1960 e consiste em um conjunto de documentos bibliográficos e suas referências bibliográficas.

A coleção CISI contém cerca de 1500 documentos, principalmente artigos científicos de áreas como ciência da computação, matemática, física e engenharia. Cada documento é acompanhado de um conjunto de metadados, incluindo informações sobre autor, título, resumo e data de publicação.

Além dos documentos em si, a coleção CISI também contém um conjunto de consultas de busca, que foram criadas para avaliar o desempenho dos sistemas de recuperação de informações. Essas consultas são compostas por um conjunto de palavras-chave que os usuários podem usar para pesquisar documentos na coleção.

A coleção CISI tem sido amplamente utilizada como um conjunto de dados de referência para avaliar a precisão e eficiência dos sistemas de recuperação de informações. Ela também tem sido usada para avaliar e comparar diferentes algoritmos e técnicas de recuperação de informações, incluindo o algoritmo clássico TF-IDF e o algoritmo BM25. A coleção CISI ainda é amplamente utilizada como um conjunto de dados de referência para pesquisadores e desenvolvedores de sistemas de recuperação de informações.

# Biblioteca Whoosh

Whoosh é uma biblioteca em Python para construir sistemas de recuperação de informação de texto. Ela fornece uma estrutura flexível para indexação e pesquisa de documentos, permitindo que os desenvolvedores criem seus próprios sistemas de busca personalizados.

A biblioteca Whoosh suporta vários recursos, incluindo:

    - Indexação eficiente e escalável de documentos
    - Consultas flexíveis, incluindo consultas por palavra-chave, frases e consultas complexas
    - Ajuste de relevância com pontuação BM25 e outras métricas
    - Suporte para pesquisa de texto completo, pesquisa fonética e pesquisa de sugestão
    - Suporte para consulta de faceta e agrupamento de resultados
    - Integração com várias fontes de dados, incluindo arquivos de texto, HTML, XML e banco de dados
    - Uma API simples e fácil de usar para construir e manipular índices.

A biblioteca Whoosh é uma opção popular para a construção de sistemas de busca e recuperação de informações em Python. Ela é usada em vários aplicativos, incluindo motores de busca na web, sistemas de gerenciamento de documentos, sistemas de recomendação e outros aplicativos de processamento de linguagem natural

A biblioteca Whoosh suporta o algoritmo de pontuação de relevância BM25 (Best Matching 25) para ajustar a relevância dos resultados da pesquisa. Na Whoosh, é possível usar o BM25 como método de ajuste de relevância ao criar um objeto searcher e passando um objeto BM25F como argumento para o parâmetro score, facilitando o projeto como um todo.

# Implementação

A estrutura do projeto seguiu os passos mencionados na introdução:

    - Baixar a coleção da web;
    - Indexar toda a coleção;
    - Receber uma entrada do usuário/filtrar as palavras-chave dessa entrada;
    - Realizar uma busca nos arquivos indexados 

Cada célula do Google Colab representa uma parte desse código, para facilitar a leitura e modularizar o projeto. A modularização ajudou a debugar durante o desenvolvimento.

As 3 ultimas partes da lista acima são as de maior interesse:

## Indexação

O código de indexação gera uma função index_cisi_collection() que cria um índice de pesquisa com a biblioteca Whoosh a partir da coleção CISI. A função realiza todo o processo de leitura, separação dos documentos, extração dos campos relevantes e adição dos documentos ao índice, para que possam ser consultados posteriormente por meio de uma pesquisa de texto.

A estrutura do indice é definida por um objeto Schema, com os campos "id", "title", "author" e "abstract". O diretório do índice é criado se não existir, e um objeto Index é criado usando o método create_in() passando o esquema como argumento. Os campos são separados pela seguinte estrutura:

    - Identificador do documento (campo .I no arquivo de texto da coleção)
    - Título do documento (campo .T)
    - Autor(es) do documento (campo .A)
    - Fonte do documento (campo .B)
    - Resumo do documento (campo .W)
    - Texto completo do documento (após o campo .X)

## Input do usuário

O código de input do usuário tem como objetivo receber uma frase do usuário, identificar as palavras mais importantes da frase e retorná-las em uma lista.

Para isso, utilizado o módulo "string" do Python. Em seguida, é definida a função "highlights", que realizará a entrada da informação e a separação das palavras mais significativas.

Foi definida uma lista de palavras comuns em inglês que serão ignoradas pelo programa, chamada "stop_words". Essas palavras geralmente não acrescentam valor semântico à frase e podem ser desconsideradas na análise. As palavras estão em inglês pois a coleção CISI está em inglês.

Foi criado um dicionário vazio chamado "word_counts", que será usado para contar a frequência das palavras na frase do usuário.

A variável "words" é criada a partir da entrada do usuário, transformada em letras minúsculas e dividida em palavras individuais. O código percorre cada uma dessas palavras e adiciona a sua frequência no dicionário "word_counts", a menos que a palavra esteja na lista "stop_words" ou seja uma pontuação.

Por fim, as palavras mais importantes são adicionadas a uma lista chamada "results" e retornadas pela função. A ordem das palavras na lista é determinada pela frequência em que aparecem na frase, com as mais frequentes no topo da lista.

## Busca 

A busca utiliza, novamente, a biblioteca Whoosh para realizar uma pesquisa em um índice de documentos.

A função parser recebe uma lista de strings de busca search_strings. Ela abre o índice de busca, define o esquema de consulta com três campos ("abstract", "author", "id"), define o algoritmo BM25F como o algoritmo de pontuação e cria uma lista de queries a partir das strings de busca fornecidas. Em seguida, as queries são unidas em uma única query usando o operador OR.

A função então executa a consulta no índice e retorna os resultados. Para cada resultado, a função imprime as informações relevantes de cada documento, incluindo o ID do documento, o título, o autor, o resumo, a pontuação de relevância e uma separação visual, no caso "__________________________//____________________"


# Exemplos

Para rodar o projeto, basta executar a utlima célula do google Colab. Essa célula roda as 3 funções definidas anteriormente na ordem que foram feitas para serem rodadas e indaga ao usuário qual será a entrada no dispositivo de buscas. Buscas especificas  (como uma linha retirada diretamente do abstract de um dos documentos ou um titulo de um documento) retornaram menos resultados, enquanto buscas mais genéricas (com um tema ou palavra) retornaram mais resultados. 

## Exemplo 1

![Captura de tela 2023-02-22 202126](https://user-images.githubusercontent.com/114251488/220789184-56de76f0-f157-4159-9d78-6f8a69cad6f2.png)

![Captura de tela 2023-02-22 202337](https://user-images.githubusercontent.com/114251488/220790317-ba47fef8-52e9-49ec-a56d-d1db4ca4ecae.png)

## Exemplo 2

![3](https://user-images.githubusercontent.com/114251488/220789510-9d8f29bc-fe3d-4415-bd6c-ae70a0c45fa2.png)
3b31a5a5.png)

![4](https://user-images.githubusercontent.com/114251488/220789515-1271277c-2039-4f02-a31e-d942f46fae5e.png)

# Auxilio ChatGPT


Como não tinha experiencia prévia alguma com o tema "Information Retrieval", tampouco "BM25", minha primeira busca no ChatGPT foi:

    "Oque é BM25?"

Após uma breve explicação, as proximas perguntas foram mais relacionadas a como realizar o projeto:

    "Como implementar um sistema de Information Retrival em python usando BM25?"

A resposta do chat foi:

    "Para implementar um sistema de Information Retrieval (Recuperação de Informação) em Python usando o modelo GPT-3 e o algoritmo BM25, você precisaria seguir os seguintes passos:

    - Preparar os dados: Para criar um sistema de recuperação de informações, você precisará de um conjunto de dados contendo os documentos que deseja indexar. Esses documentos podem ser textos de sites da web, artigos, livros ou qualquer outra coisa que você queira indexar. Para este exemplo, vamos usar um conjunto de dados de artigos sobre tecnologia.

    - Indexar os documentos: Para indexar os documentos, você pode usar uma biblioteca de indexação, como o Whoosh ou o ElasticSearch. Essas bibliotecas são capazes de extrair informações dos documentos, como os termos que aparecem nos documentos e a frequência com que aparecem. Eles também permitem que você armazene essas informações em um formato que permita consultas rápidas.

    - Implementar o algoritmo BM25: Para implementar o algoritmo BM25, você pode usar a biblioteca python-whoosh, que fornece uma implementação do BM25. Você precisará calcular o BM25 para cada termo da consulta em relação a cada documento indexado. A biblioteca python-whoosh permite que você calcule o BM25 com base nos termos da consulta e nos termos indexados nos documentos.

    - Retornar os resultados: Depois de calcular o BM25 para cada documento, você precisará retornar os resultados ao usuário. Os resultados podem ser classificados com base na pontuação BM25 ou em qualquer outra métrica que você preferir. Você pode retornar uma lista dos documentos mais relevantes ou exibir um snippet do texto em cada documento.

    Observe que a implementação de um sistema de recuperação de informações é um processo complexo e requer conhecimento de várias tecnologias e algoritmos. O processo acima é apenas um exemplo simples para ilustrar o fluxo de trabalho básico."

Sabendo os passos que deveria seguir para realizar o projeto, perguntei tambem quais bibliotecas ele recomendava para a tarefa, porém a resposta foi mais complexa do que a necessária:

    "Para implementar um sistema de Information Retrieval em Python usando GPT-3 e BM25, recomendo o uso das seguintes bibliotecas:

    Hugging Face Transformers: É uma biblioteca de aprendizado profundo (deep learning) que inclui modelos de linguagem de última geração, incluindo o GPT-3. A biblioteca facilita o carregamento e uso do GPT-3 e outros modelos de linguagem em Python.

    Whoosh: É uma biblioteca de indexação em Python que permite indexar e pesquisar documentos em Python. É fácil de usar e oferece uma implementação do algoritmo BM25 para classificar documentos.

    NLTK (Natural Language Toolkit): É uma biblioteca de processamento de linguagem natural em Python que fornece recursos para pré-processamento de texto, tokenização, análise sintática e outras tarefas relacionadas à linguagem natural.

    Pandas: É uma biblioteca de análise de dados em Python que permite manipular e analisar dados em Python. É útil para carregar e manipular dados de documentos e conjuntos de dados.

    Flask: É um framework web em Python que permite construir aplicativos web com facilidade. É útil para criar uma interface do usuário para o sistema de recuperação de informações.

    Essas bibliotecas são amplamente usadas na comunidade de ciência de dados e aprendizado de máquina em Python e têm documentação e recursos excelentes disponíveis online para ajudá-lo a começar."

Foi dessa forma que chegamos a bibliteca Whoosh, fundamental para a elaboração desse projeto. As proximas perguntas foram focadas em pedir exemplos de como indexar e realizar buscas utilizando o whoosh, pedindo exemplos e explicações sobre cada objeto e metodo utilizado. Um pdf com o historio de buscas no chatGPT para a realização desse projeto estará dentre os arquivos do github.
