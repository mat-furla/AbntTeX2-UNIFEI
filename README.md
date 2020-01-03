# AbnTeX2-UNIFEI


# Apresentação


O presente projeto tem o objetivo de fornecer uma série de modificações do pacote AbnTeX2 para LaTeX incluindo novos comandos, capa e folha de rosto personalizadas para a Universidade Federal de Itajubá - UNIFEI. Grande parte dessas modificações foram retiradas do pacote [abntex2-pucminas](https://github.com/abntex/abntex2-contrib/blob/master/customizacoes/pucminas/abntex2-pucminas.sty).
Além disso o presente documentará diversas dicas e uso de outros pacotes de modo a facilitar e adicionar funcionalidades ao LaTeX. Espero que o documento seja útil para universitários da UNIFEI que buscam utilizar a ferramenta, porém ainda tem muitas dúvidas de como proceder.


# Instalação do LaTeX


Para começar a utilizar o pacote necessita-se primeiramente instalar alguma distribuição TeX no seu sistema operacional, esta secção tratará somente da instalação no Windows, caso utilize outro por gentileza procure mais informações na página -> [link](https://www.latex-project.org/get/).

### MikTeX

MiKTeX é uma distribuição TeX/LaTeX para Microsoft Windows, a mesma fornecerá uma instalação com todos os pacotes necessários para iniciar um documento LaTeX.
Primeiramente acesse o [link](https://miktex.org/download)  e faça o download do pacote. Instale como qualquer programa. Ao final da instalação abrirá uma janela procurando por atualizações dos pacotes, instale todas as disponíveis.

### TeXstudio

TeX é um formato de texto puro, podendo ser escrito em qualquer editor, porém alguns feitos especialmente para esse fim facilitam a tarefa, incluindo syntax highlighting, visualizador de pdf integrado, checagem por referências, etc.
O editor da minha escolha é o TeXstudio, que pode ser encontrado no [link](https://www.texstudio.org/). Proceda com a instalação normalmente, ao final do procedimento o editor estará instalado e pronto para começar com os documentos.


Usando AbnTeX2-UNIFEI
-------

O uso do AbnTeX2-UNIFEI é extremamente simples, apenas é necessário que o arquivo *unifei.sty* esteja no mesmo diretório onde os arquivos estão sendo editados, depois disso é necessário incluir no preâmbulo o comando: `\usepackage{unifei}`. Para o uso do AbnTeX2-UNIFEI o pacote AbnTeX2 já tem que estar sendo utilizado no documento.

Se preferir o presente repositório contém um modelo para trabalho científico, com grande parte dos secções já incluídas. O documento está dividido em alguns arquivos:
- **config.tex**: Onde está contido o preâmbulo do documento, com todas as configurações de pacotes e as informações da capa e folha de rosto;
- **pretextual.tex**: Possui todos os comandos para os elementos pré-textuais da ABNT, incluindo:
   - Capa;
   - Folha de rosto;
   - Dedicatória;
   - Agradecimentos;
   - Epígrafe;
   - Resumo em língua vernácula;
   - Resumo em língua estrangeira;
   - Lista de ilustrações;
   - Lista de tabelas;
   - Lista de abreviaturas e siglas;
   - Lista de símbolos;
   - Sumário.
- **main.tex**: é o documento principal onde todos os outros são incluídos e onde o texto em si será feito, contendo:
   - Introdução;
   - Desenvolvimento;
   - Conclusão.
- **postextual.tex**: onde estão presentes os elementos pós-textuais, incluindo:
   - Referências;
   - Glossário;
   - Apêndices;
   - Anexos.
- **referencias.bib**: contém todas as referências citadas durante o texto.

### Adicionais do pacote

O AbnTeX2-UNIFEI fornece os seguintes comandos adiconais:

```
\departamento{nome do departamento} % o nome do departamento
\subtitulo{Subtitulo do trabalho} % como o título deve ser em caixa alta, mas o subtitulo não, há esse novo comando (ele inclui o : ao final do título)
%---
\foa % equivale a {\legend{Fonte: Elaborada pelo autor.}}
\fad{cite} % equivale a {\legend{Fonte: Adaptada de \citeonline{cite}.}}
\fod{cite} % equivale a {\legend{Fonte: \citeonline{cite}.}}
\fodp % equivale a {\legend{Fonte: Dados da pesquisa.}}
```

Dicas
-------

### Inclusão de código fonte no documento
Se você tem a necessidade de incluir alguns tipos de código fonte com syntax highlighting no seu documento, recomendo utilizar o pacote **minted**.
Para isso inclua no preâmbulo do seu documento:

```
\usepackage{minted}
\setminted{frame=lines, framesep=2mm,baselinestretch=1,linenos}
```

Também é possível escolher diferentes temas para destaque, para modificar o tema padrão também inclua:

```
\usemintedstyle{nome_do_tema}
```

Modifique nome do tema com algum dos disponíveis [aqui](https://pygments.org/demo/).

Para usar o pacote:

```
\begin{minted}{nome_da_linguagem}
#Adicione o código fonte aqui
\end{minted}
```

As linguagens disponíveis estão listadas [aqui](https://pygments.org/languages/).
Caso utlize algumas linguagens relacionadas a Angular e o pdf gerado contém várias marcas vermelhas no código, experimente adicionar o seguinte antes do `\begin{minted}{nome_da_linguagem}`:

```
\makeatletter
\expandafter\def\csname PYGdefault@tok@err\endcsname{\def\PYGdefault@bc##1{##1}}
\makeatother
```