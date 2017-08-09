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
describe CHECK_CAUMA  Existem URL maliciosas em seu e-mail

describe CAUMA_LOGIN  *colocar login informado pelo CERT.Bahia*
describe CAUMA_KEY    *colocar key informado pelo CERT.Bahia*
```

## Ativa��o no Zimbra

```
wget https://raw.githubusercontent.com/UniversidadeFederalDoRioGrandeFURG/spamassassin-cauma/master/cauma.pm -O /opt/zimbra/common/lib/perl5/Mail/SpamAssassin/Cauma.pl
```

# editar /opt/zimbra/data/spamassassin/v310.pre
```
loadplugin CaUMa /opt/zimbra/common/lib/perl5/Mail/SpamAssassin/Cauma.pl
```

```
cat <<EOF > /opt/zimbra/data/spamassassin/cauma.cf
body CHECK_CAUMA eval:check_cauma()
score CHECK_CAUMA 10
describe CHECK_CAUMA  Existem URL maliciosas em seu e-mail

describe CAUMA_LOGIN  *colocar login informado pelo CERT.Bahia*
describe CAUMA_KEY    *colocar key informado pelo CERT.Bahia*
EOF
```
