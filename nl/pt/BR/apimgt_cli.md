---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Comandos de gerenciamento de API do Bluemix
{: #apimgt_cli}

Versão: 1.0.0

É possível instalar o plug-in da interface da linha de comandos (CLI) de gerenciamento da API do
{{site.data.keyword.Bluemix_notm}} para concluir ações de gerenciamento
comuns para APIs com script. As informações a seguir listam os comandos que estão
incluídos no plug-in da CLI de gerenciamento da API, incluindo seus nomes, opções, uso,
pré-requisitos, descrições e exemplos.
{:shortdesc}

**Nota:** **Pré-requisitos** listam quais ações são necessárias antes de usar o comando. Os comandos que não têm ações de pré-requisito listam **Nenhum**. Caso contrário, os pré-requisitos podem incluir uma ou mais das ações a seguir:

**Nota:** Você pode utilizar o formato curto de comandos
bluemix; por exemplo, `bx apim` é abreviação de `bluemix
apim`.

Utilize os índices na tabela a seguir para consultar os comandos de gerenciamento
de API usados frequentemente.

<table summary="Comandos de gerenciamento de API.">
<caption>Tabela 1. Comandos de gerenciamento de API</caption>
 <thead>
 <th colspan="5">Comandos de gerenciamento de API</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim help](apimgt_cli.html#apim_help)</td>
 <td>[bluemix apim api](apimgt_cli.html#apim_api)</td>
 <td>[bluemix apim apis](apimgt_cli.html#apim_apis)</td>
 <td>[bluemix apim api-create](apimgt_cli.html#apim_api-create)</td>
 <td>[bluemix apim api-delete](apimgt_cli.html#apim_api-delete)</td>
 <td>[bluemix apim api-expose](apimgt_cli.html#apim_api-expose)</td>
 <td>[bluemix apim api-share](apimgt_cli.html#apim_api-share)</td>
 <td>[bluemix apim api-unexpose](apimgt_cli.html#apim_api-unexpose)</td>
 <td>[bluemix apim api-unshare](apimgt_cli.html#apim_api-unshare)</td>
 <td>[bluemix apim api-update](apimgt_cli.html#apim_api-update)</td>
 <td>[bluemix apim keys](apimgt_cli.html#apim_keys)</td>
 </tr>
 </tbody>
 </table>
 
  
## Ajuda de gerenciamento de API
{: #apim_help}
Exiba a ajuda geral para comandos integrados de primeiro nível e namespaces suportados
da CLI de gerenciamento de API, ou a ajuda para um comando específico integrado ou
namespace.

### Sintaxe

```
bluemix apim help <object-action>
```
{: codeblock}

### Opções de comando

   <dl>
   <dt>objeto-ação (opcional)</dt>
   <dd>O comando para o qual a ajuda é exibida. Se não especificado, a ajuda geral para a
CLI de gerenciamento de API será mostrada.</dd>
   </dl>

### Exemplos

Exibir a ajuda geral para a CLI de gerenciamento de API:

```
bluemix apim help
```

Exibir ajuda para o comando `api-create`:

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Exibir as propriedades de uma API gerenciada.

### Sintaxe
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Sinalização necessária
   <dl>
   <dt>--name</dt>
   <dd>Especifica o nome da API gerenciada</dd>
   </dl>


### Opções de comando
   <dl>
   <dt>--swagger</dt>
   <dd>Exibe as informações do documento de definição Open API na saída</dd>
   </dl>

### Saída

O comando exibe uma tabela que lista as seguintes informações sobre a API especificada:

   <dl>
     <dt>Nome</dt>
	 <dd>O nome da API.</dd>
	 <dt>Tipo</dt>
	 <dd>O tipo de API. As entradas válidas são <em>whisk</em>, <em>cf-apps</em> ou <em>definido pelo usuário</em></dd>
	 <dt>Gerenciado</dt>
	 <dd>Se o valor for true, indica que o terminal foi descoberto, mas não exposto no gateway.</dd>
	 <dt>Exposto</dt>
	 <dd>Indica se a API está ativa no gateway (<em>true</em>) ou não (<em>false</em>).
	 <dt>Compartilhado</dt>
	 <dd>Indica se a API é compartilhada fora de sua organização Bluemix (<em>true</em>) ou não (<em>true</em>).</dd>
	 <dt>URL gerenciada</dt>
	 <dd>Especifica o local da versão compartilhada da API.</dd>
   </dl>

   
### Exemplos

Exibir as propriedades da API denominada cloudfound1:

```
bluemix apim api cloudfound1
```

Exibir os conteúdos do arquivo de definição e propriedades para a API denominada api2:

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


Liste as APIs que estão disponíveis e identificadas no servidor de terminal identificado.

### Sintaxe
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Opções de comando

Nota: Se nenhuma opção for especificada, as informações para todas as APIs serão
retornadas.
   <dl>
   <dt>--api-provider </dt>
   <dd>Só retorna os tipos de APIs que você especifica aqui. As opções válidas são
<em>whisk</em> para as APIs Openwhisk, <em>cf-apps</em> para APIs do aplicativo Cloud
Foundry e <em>definido pelo usuário</em> para APIs que não estão associadas a Openwhisk
ou Cloud Foundry.</dd>
   <dt>--exposed</dt>
   <dd>Apenas retorna APIs que são expostas.</dd>
   <dt>--shared</dt>
   <dd>Apenas retorna APIs que são compartilhadas fora de sua organização.
{{site.data.keyword.Bluemix_notm}}</dd>
   </dl>

### Saída

O comando exibe uma tabela que lista as seguintes informações sobre as APIs
especificadas:

   <dl>
     <dt>Nome</dt>
	 <dd>O nome da API.</dd>
	 <dt>Tipo</dt>
	 <dd>O tipo de API. As entradas válidas são <em>whisk</em>, <em>cf-apps</em> ou
<em>definido pelo usuário</em></dd>
	 <dt>Managed</dt>
	 <dd>Se o valor for true, indica que o terminal foi descoberto, mas não exposto no
gateway.</dd>
	 <dt>Exposto</dt>
	 <dd>Indica se a API está ativa no gateway (<em>true</em>) ou não (<em>false</em>).
	 <dt>Compartilhado</dt>
	 <dd>Indica se a API é compartilhada fora de sua organização Bluemix (<em>true</em>) ou não (<em>false</em>).</dd>
	 <dt>URL gerenciada</dt>
	 <dd>Especifica o local da versão compartilhada da API se a API for exposta. O valor é
<em>indefinido</em> quando a API não é exposta. </dd>
   </dl>


### Exemplos

Retornar todas as APIs que estão disponíveis no gerenciador de terminal:

```
bluemix apim apis 
```

Retornar todas as APIs OpenWhisk que estão disponíveis:

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Torna uma API existente não gerenciada em uma API gerenciada importando seu arquivo Swagger.

### Sintaxe

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Sinalizações necessárias

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja gerenciar.</dd>
   <dt>--file</dt>
   <dd>Fornece o caminho para o arquivo de definição Open API, que está no formato JSON ou YAML.</dd>
   <dt>--provider</dt>
   <dd>Especifica o tipo de API que você está criando. Nota: A única entrada válida para isso é <em>cf-apps</em>.
   </dl>

### Opção de comando

   <dl>
   <dt>--expose</dt>
   <dd>Exponha o terminal automaticamente depois de criá-lo.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Criado com êxito
* Erro (com a descrição do erro)

### Exemplos

Gerenciar uma API do Cloud Foundry denominada apinumber1 que tenha um arquivo de definição yaml chamado reservations1:

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Gerenciar um aplicativo Cloud Foundry chamado cfapi que tenha um arquivo de definição json chamado definition1:

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Remove uma API gerenciada do banco de dados.

### Sintaxe

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Sinalizações necessárias

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja excluir. **Importante:**
Excluir a API do Cloud Foundry remove a API do estado gerenciado, mas o app Cloud Foundry
não é excluído. A exclusão de uma API OpenWhisk exclui a API inteira e deve ser recriada
após ser excluída.</dd>
   <dt>--confirm</dt>
   <dd>Confirma que o comando deve ser concluído sem fornecer um prompt de confirmação.</dd>
   </dl>


### Saída

O comando envia as seguintes informações:
* Excluído com êxito
* Erro (com a descrição do erro)

### Exemplos

Excluir a API cloudapi1 do Cloud Foundry:

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Torna uma API gerenciada visível a outros dentro da minha organização.
{{site.data.keyword.Bluemix_notm}}

### Sintaxe
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Sinalização necessária

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja expor.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Exposto com êxito
* Erro (com a descrição do erro)

### Exemplo

Expor uma API do Cloud Foundry chamada cloudfound1 com minha organização
{{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Torna uma API gerenciada visível a outros fora da minha organização.
{{site.data.keyword.Bluemix_notm}}

### Sintaxe
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Sinalização necessária

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja compartilhar.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Compartilhado com êxito
* Erro (com a descrição do erro)

### Exemplo

Compartilhar uma API do Cloud Foundry chamada cloudfound1 fora da minha organização
{{site.data.keyword.Bluemix_notm}}:
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Torna uma API gerenciada que é visível a outros dentro de sua organização
{{site.data.keyword.Bluemix_notm}} não mais visíveis a outros.

### Sintaxe
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Sinalização necessária

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja remover da visibilidade de outros em sua
organização {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Exposto com êxito
* Erro (com a descrição do erro)

### Exemplo

Remover uma API OpenWhisk chamada openwhisk1 da visualização para outros membros da
minha organização {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Remove da visibilidade uma API gerenciada que é visível a outros fora da minha organização
{{site.data.keyword.Bluemix_notm}}.

### Sintaxe
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Sinalização necessária</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja parar de compartilhar.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Compartilhamento cancelado com êxito
* Erro (com a descrição do erro)

### Exemplo

Parar de compartilhar uma API do Cloud Foundry chamada cloudfound1 fora da minha
organização {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Atualiza as configurações de uma API gerenciada, substituindo seu arquivo de
definição. Importante: Esta é uma substituição completa das definições existentes na API
pelas definições no novo arquivo. Quaisquer entradas vazias ou ausentes no novo arquivo que
existirem no arquivo existente serão removidas da definição.

### Sintaxe
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Sinalizações necessárias

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica o nome da API que você deseja atualizar.</dd>
   <dt>--file</dt>
   <dd>Fornece o caminho para o arquivo de definição Open API de substituição, que está no formato JSON ou YAML.</dd>
   </dl>

### Saída

O comando envia as seguintes informações:
* Atualizado com êxito
* Erro (com a descrição do erro)


### Exemplo

Atualizar uma API OpenWhisk chamada whiskapi1 com um arquivo de definição com o nome definition1.json:

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Exibe as propriedades de chaves que estão associados a uma API gerenciada.

### Sintaxe
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Sinalizações necessárias

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Especifica o nome da API que você deseja expor.</dd>
   <dt>--bluemix</dt>
   <dd>Lista as chaves API do {{site.data.keyword.Bluemix_notm}} para a API especificada.</dd>
   <dt>--external</dt>
   <dd>Lista as chaves API externas para a API especificada.</dd>
   </dl>

### Saída

O comando exibe uma tabela que lista as seguintes informações sobre as APIs especificadas:


   <dl>
     <dt>Nome da Chave</dt>
	 <dd>O nome da chave API.</dd>
	 <dt>Tipo de chave</dt>
	 <dd>O tipo de chave API. As entradas válidas são <em>bluemix</em> e <em>externo</em>.</dd>
	 <dt>ID do cliente</dt>
	 <dd>O nome do cliente que é identificado com a chave.</dd>
	 <dt>Segredo fornecido</dt>
	 <dd>Indica se o segredo da API é fornecido para a API. Os valores possíveis são
<em>true</em>, se houver um segredo, e <em>false</em> se não houver nenhum segredo.
   </dl>


### Exemplos

Retornar todas as chaves externas associadas à API denominada cloudfound1.

```
bluemix apim --name cloudfound1 --external
```

Retornar as chaves para permitir que as pessoas dentro da minha organização
{{site.data.keyword.Bluemix_notm}} vejam minha API denominada myapi1.

```
bluemix apim --name myapi1 --bluemix 
```
 
