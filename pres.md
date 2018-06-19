# Sphinx

## Índice

* Introdução
* Instalação
* Sphinx no kernel
* Atividade

## Sphinx

* Desenvolvido para fazer a documentação do python (https://docs.python.org/3/)

* Suporte para documentar projetos em diversas linguagens

# Algumas características

## Formatos de saída

* html
* latex
* epub
* ...

## Referências cruzadas

* linguagem de marcação (markup) semântico
* links automáticos para funções, classes, citações, glossários

## Estrutura hierárquica

* Simples definição de árvores de documentos 
* Links automáticos para filhos, pais, ...

## Índices automáticos

* .

## Highlight de código automático

* . 

## Extensões

* Testes de pedações de códigos (snippets)
* Inclusão de docstring de módulos python

## Formatos/Ferramentas

* reStructuredText
* Docutils

## Instalação

* pip3 install sphinx

## Um pouco de sintaxe

* TODO

# Referências específicas para o Kernel

## Instalação para documentação do kernel

* Documentação do kernel sugere utilizar um ambiente virtual

`$ virtualenv sphinx_1.4

$ . sphinx_1.4/bin/activate

(sphinx_1.4) $ pip install -r Documentation/sphinx/requirements.txt
`

* Para trabalhar com imagens instalar pacotes GraphViz e ImageMagick (irão dar
  suporte à GraphViz e arquivos svg)

* Script para verificar dependências do sphinx: /scripts/sphinx-pre-install

## Gerando documentação do Kernel

* make htmldocs
* make pdfdocs
* Documents/output
* para limpar: make cleandocs
* passar configurações para o sphinx : 


## Configuração de projeto

* sphinx-quickstart
* cria pastas e arquivos básicos


### conf.py

* configuraçoẽs gerais
* quais módulos vão estar habilitados
* ...

## Escrevendo documentação para o kenel

* Passos simples:
    * Adicionar um arquivo .rst em algum lugar de Documentation
    * Referenciar esse arquivo na TOC Tree principal de Documentation/index.rst

* Em alguns casos uma pasta específica (como subsistema de gpu), com index.rst
  próprio

## Diretrizes específicas para o kernel

* Não extrapole no uso do reStructuredText. Mantenha simples.
* Mantenha modificações de formato mínimo quando for converter documentação
  existente para rSt

* Atualize também o conteúdo, quando for converter

## Diretrizes específicas para o kernel

* Matenha essa ordem para sintaxe de títulos:

```
===================
Título de documento
===================
```


```
Capítulos
=========
```

```
Seção
-----
```

```
Sub-seção
~~~~~~~~~
```


## Diretrizes específicas para o kernel

* Para trechos de código (que não se beneficiem de "highlight") use `::`

* Para trechos de código maiores, que se beneficiem de "highlight" use `..
  code-block:: <language> `


## The C Domain

* TODO

## list tables

* Para tabelas é recomendado _list tables_, ao invés do ASCII-art
* É fácil d criar e modificar, é o diff tem muito mais significado 

## flat table

* é uma lista de dois estágios similiar à list tables, com algumas
  características adicionais:
    * cspan: permite que uma celula seja extendida através de colunas
      adicionais
    * rspan: idem, porém através de linhas
    * _auto span_ : padrão é estender a celula à direita, caso nem todas as
      celulas estejam definidas
    * pode-se usear _fill cells_ para que sejam criadas celulas vazias ao invés
      de estender

## flat table - exemplo

```rst
.. flat-table:: table title
   :widths: 2 1 1 3

   * - head col 1
     - head col 2
     - head col 3
     - head col 4

   * - column 1
     - field 1.1
     - field 1.2 with autospan

   * - column 2
     - field 2.1
     - :rspan:`1` :cspan:`1` field 2.2 - 3.3

   * .. _`last row`:
     - column 3
```

## flat table - exemplo

![Tabela de Exemplo](table.png)


## Figuras e Imagens

* Usar diretivas kernel-figure e kernel-image
* Para imagem, usar formato SVG, e diretiva kernel-image

```
.. kernel-figure::  svg_image.svg
   :alt:    simple SVG image

   SVG image example
```

## Figuras e Imagens

* Aceita formato DOT também
* http://graphviz.org/pdf/dotguide.pdf

## Figuras e Imagens

* É possível inserir figuras e imagens "embutidas"

```
   :alt: foobar digraph
   :caption: Embedded **DOT** (Graphviz) code

   digraph foo {
    "bar" -> "baz";
   }
```


