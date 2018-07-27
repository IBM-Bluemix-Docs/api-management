---

copyright:
  years: 2017
lastupdated: "2017-07-25"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Executar comandos com a CLI de gerenciamento de API
{: #apim-cli-over}

É possível utilizar a CLI de gerenciamento de API do
{{site.data.keyword.Bluemix_notm}} para concluir algumas das mesmas tarefas com a
linha de comandos que você pode concluir com a interface gráfica com o usuário do
{{site.data.keyword.Bluemix_notm}}. Os comandos podem ser inseridos
individualmente em uma janela do terminal ou chamados em uma sequência em um script. 
{:shortdesc}

## Pré-requisitos
{: #apim-cli-script-prereq}

Para poder usar a CLI de gerenciamento de API, deve-se ter concluído as seguintes etapas:

* Obtenha um [ID do Bluemix](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Faça download e instale a [linha de comandos do Bluemix](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Instale o [plug-in da linha
de comandos de gerenciamento de API](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window} do {{site.data.keyword.Bluemix_notm}}.
* [Efetue
login](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} na linha de comandos do {{site.data.keyword.Bluemix_notm}}

## Sequência de comandos de amostra da CLI para uma API

As seguintes etapas demonstram um ciclo completo de comandos de gerenciamento de
API da inclusão de um gateway em uma API até a remoção do gateway da API:

1. Efetue login no {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Registre-se na organização padrão {{site.data.keyword.Bluemix_notm}} com a interface da linha de comandos.

2. Exiba suas APIs
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Exibe as APIs em sua organização padrão.

3. Criar uma API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Usa o arquivo Swagger para criar uma API gerenciada da API que você especifica em sua
organização {{site.data.keyword.Bluemix_notm}}.

4. Atualizar uma definição de API existente
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Substitui a definição existente da API que você especifica pela nova definição de arquivo Swagger.

5. Expor a API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Expõe a API.

6. Compartilhar a API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Compartilha a API com outras pessoas fora da sua organização
{{site.data.keyword.Bluemix_notm}}.

7. Parar de expor a API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Para de compartilhar a API fora da sua organização {{site.data.keyword.Bluemix_notm}}.

8. Exibir as chaves para sua API
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Exibe as chaves que estão associadas à sua API, se houver alguma.

9. Parar de compartilhar a API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Para de compartilhar a API.
	
10. Remover a API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Remove o gateway da API. Ele não é mais gerenciado. 
    Importante: Se você excluir uma API do Cloud Foundry, o app Cloud Foundry base
permanecerá no serviço do {{site.data.keyword.Bluemix_notm}}, mas não será mais
gerenciado. Uma API OpenWhisk que é excluída remove todas as interações entre as ações
individuais do OpenWhisk. Após a API OpenWhisk ser excluído, ela deverá ser recriada se
você quiser usá-la novamente.
    
Consulte [Comandos
da interface da linha de comandos](../../cli/plugins/api-management-cliplugin/index.html) para obter a lista completa de comandos de
gerenciamento de API e suas opções.

