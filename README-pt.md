# Certbot Guia-rápido (rascunho v0.1)

[`Certbot`](https://pt.wikipedia.org/wiki/certbot) é um software de linha de comando usado em servidores Web, e faz parte do esforço da [EFF](https://www.eff.org) para criptografar toda a Internet.

Este guia é destinado a usuários iniciantes e experientes que precisam de uma referência rápida porém aderente aos seus casos de uso. 
Para qualquer detalhe, consulte a **documentação completa do `certbot`** em [certbot.eff.org/docs](https://certbot.eff.org/docs).

NOTAS

Este guia foi elaborado com base nos comandos mais frequentemente utilizados do `certbot`. 
Esse "frequentemente" não é um resultado estatístico, mas uma percepção da comunidade ativa.
É também uma compilação dos *[Casos de Uso](https://en.wikipedia.org/wiki/Use_case) mais comuns* do software `certbot`. 

Quando em dúvida sobre alguma *decisão de projeto* ou excesso de detalhes no texto, 
adota-se o princípio da [convenção sobre configuração](https://pt.wikipedia.org/wiki/Conven%C3%A7%C3%A3o_sobre_configura%C3%A7%C3%A3o) 
para evitar múltiplas recomendações, deixando os demais detalhes como "dica".

O guia foi organizado em *cenários* de casos de uso, fornecendo o comando ou seqüência de comandos para cada caso de uso.


(Tabela de Contéudos pendente aqui)

-----

## Instalar certbot

Use o formulário *"Estou usando ..."* em https://certbot.eff.org

## Cenário 1

Suponha que você tenha quatro domínios a certificar, e o "domínio mais importante" também o nome do certificado,

* ** Nome do Certificado **: `xxxx.org`
* ** Lista de domínio ** (de um ou mais): `xxxx.org aaaaa.com aaaaa.org bbbbb.com

### Criando um certificado com um domínio

Comando: `certbot --cert-name xxxx.org -d xxxx.org`

Dica: use escolher "Seguro" ao selecionar a estratégia de redirecionamento HTTPS.

### Criando um certificado com muitos domínios

Comando: `certbot --cert-name xxxx.org -d xxxx.org -d aaaaa.com -d aaaaa.org`.

Dica: o primeiro (`xxxx.org`) é o * Nome do Certificado *.

### Atualizando o certificado uma vez

Comando: `certbot renew`

Dica: também há um *procedimento de renovação automática*, veja o caso "Atualizando o certificado para sempre".

### ... caso de uso ...
...

## Cenário-2
...
