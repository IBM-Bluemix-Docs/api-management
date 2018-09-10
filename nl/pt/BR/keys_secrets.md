---

copyright:
  years: 2017,2018
lastupdated: "2018-01-05"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gerenciar chaves e segredos
{: #keys_secrets}

Quando suas APIs são gerenciadas pelo gerenciamento de API, é possível usar chaves e segredos para controlar o acesso às APIs.

## Criando a chave e o segredo
{: #create_key_secret}

Para incluir uma chave em sua API, conclua as etapas a seguir:

1. Abra a API do {{site.data.keyword.openwhisk_short}} ou do aplicativo Cloud Foundry, caso ainda não esteja aberta.

2. Selecione *API Management* na navegação.

3. Selecione a guia Compartilhando chaves do & para acessar as chaves para
esse aplicativo ou API. *Nota: Não é possível ver as guias até que você salve seu
aplicativo ou API pela primeira vez.*

4. Assegure-se de que a régua de controle **Expor API
gerenciada** esteja configurada para a posição *ligado*. A API
deve ser exposta para que você possa designar chaves.

5. Crie uma chave para um cliente que tenha acesso à sua organização {{site.data.keyword.Bluemix_notm}}.
  1. Selecione **Criar chave API +** na seção
*Compartilhando dentro da organização {{site.data.keyword.Bluemix_notm}}*. Uma
chave e um segredo são automaticamente criados e inseridos nos campos corretos. Não é
possível atualizar a chave ou o segredo para esse tipo de chave. 
  2. Insira um nome para sua chave e segredo para ajudar a identificá-lo. Por exemplo, o
nome do cliente que vai usá-lo.
  3. Selecione **Salvar** para salvar a nova chave.
  4. Você pode repetir as etapas de *a* até *c* para chaves adicionais, se necessário. É possível ter no máximo 5 chaves nesta seção por API.

6. Crie uma chave para um cliente que não seja membro da sua organização {{site.data.keyword.Bluemix_notm}}.
  1. Selecione **Criar chave API +** na seção
*Compartilhando fora da organização {{site.data.keyword.Bluemix_notm}}*. Uma
chave é automaticamente criada e inserida no campo correto. Não há nenhum segredo exibido
inicialmente para esse tipo de chave. Não é possível atualizar a chave. 
  2. Insira um nome para sua chave para ajudar a identificá-la. Por exemplo, o
nome do cliente que vai usá-lo.
  3. Opcional: Se você desejar incluir um segredo na chave, selecione o
**Link do portal da API** para a chave na qual deseja incluir o
segredo e selecione **Configurar segredo da API**.
  4. Selecione **Salvar** para salvar a nova chave.
  5. Você pode repetir as etapas de *a* até *d* para chaves
adicionais, se necessário. É possível ter no máximo 5 chaves nesta seção por API.
Suas chaves são listadas para a API quando a guia *Compartilhamento e chaves* é selecionada.

## Especificando uma chave e um segredo em uma chamada API
{: #spec_key_secret}

Seus clientes só poderão chamar a API se eles incluírem a chave e/ou o segredo
correto no cabeçalho da chamada. Para chamar a API, eles devem incluir a chave e o segredo
na chamada API, conforme mostrado no exemplo a seguir:
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Em que *add_secret_here* é substituído pelo segredo da chave correta. 

## Excluindo uma chave API
{: #delete_key}

Em algum momento, você desejará remover uma chave. Talvez um cliente que usou sua
API crie sua própria API e não precise mais da sua. Para assegurar que nenhum de seus
clientes ainda esteja usando a API, você pode excluir a chave. Para excluir uma chave do
serviço, conclua as etapas a seguir:

1. Abra a API do {{site.data.keyword.openwhisk_short}} ou do aplicativo Cloud Foundry, caso ainda não esteja aberta.

2. Selecione *Gerenciamento de API* na navegação.

3. Selecione a guia *Compartilhando chaves do &*.

4. Localize a chave que você deseja excluir. Dica: Isso é quando é útil nomear as
chaves para que elas sejam facilmente identificadas.

5. Selecione o ícone de opções, que são três pontos verticais, ao lado da chave que você deseja excluir. 

6. Selecione **Excluir chave**.

7. Confirme a exclusão para remover a chave.
