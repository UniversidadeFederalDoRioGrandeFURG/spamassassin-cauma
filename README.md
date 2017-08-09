![alt tag](https://cauma.pop-ba.rnp.br/static/img/cauma_black.png)

Plugin de integra��o do do servi�o [CaUMa](https://cauma.pop-ba.rnp.br/about) com o [SpamAssassin](http://spamassassin.apache.org/).

## Sobre o CaUMa

CaUMa (Cat�logo de URLs Maliciosas) � um servi�o gratuito e p�blico criado pelo CERT.Bahia, que disponibiliza um meio de consulta a urls fraudulentas identificadas na Internet. O prop�sito desse servi�o � ajudar a comunidade a se proteger das diversas fraudes que est�o circulando no mundo digital.

## Pr�-requisitos

Bibliotecas REST::Client e JSON para o Perl

```
cpan REST::Client
cpan JSON
```

## Ativa��o da regra no SpamAssassin

Editar de regras do SpamAssassin e incluir a regras

```
loadplugin CaUMa /<path do script>/cauma.pm

body CHECK_CAUMA eval:check_cauma()
score CHECK_CAUMA 10
describe CAUMA_LOGIN  ...
describe CAUMA_KEY    ...
```
