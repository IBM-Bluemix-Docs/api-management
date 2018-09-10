---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Acessando mais recursos de gerenciamento de API
{: #upgrade}

A função de gerenciamento de API que é fornecida com sua API do
{{site.data.keyword.Bluemix}} permite que você limite o controle das taxas de
chamada, OAuth e visualize análises. Você pode ter maior controle de gerenciamento sobre APIs ao fazer upgrade para o serviço do {{site.data.keyword.apiconnect_full}}. O serviço do {{site.data.keyword.apiconnect_short}} fornece mais opções de políticas de segurança e maior controle sobre limites de taxa. Além disso, você será capaz de configurar um Portal do Desenvolvedor completamente customizável para que possa socializar suas APIs e participar da comunidade do desenvolvedor. Outros benefícios incluem:
* Gerenciamento do Ciclo de Vida
* APIs compostas
* Integração de serviços da web
* Mediação de protocolo
* Geração de API por meio de esquema
* Desenvolvimento de microsserviços

A migração para o serviço do {{site.data.keyword.apiconnect_short}} é fácil e não é necessário recriar nenhuma das APIs que você estiver gerenciando com o gerenciamento de API. É
possível migrar suas APIs de forma automática ou manual.

## Migrando APIs automaticamente para {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

Se você decidir fazer upgrade para {{site.data.keyword.apiconnect_short}},
precisará migrar suas APIs do gerenciamento de API para o serviço
{{site.data.keyword.apiconnect_short}} selecionando e concluindo o
procedimento a seguir para o tipo de API que você está migrando.

### API do Cloud Functions

1. Selecione **Functions** no menu {{site.data.keyword.Bluemix_notm}} para visualizar suas Cloud Functions.

2. Na lista Functions, selecione **APIs** na navegação.

3. Selecione o nome da API de função que você deseja migrar.

4. Selecione **Definição** na navegação.

5. Selecione **Arquivo de definição de API** > **Abrir no API Connect** > **Continuar** na seção *Arquivo de definição de API*. Se
você já tiver um serviço {{site.data.keyword.apiconnect_short}} existente, ele
migrará automaticamente a API para o serviço existente. Se você ainda não tiver um
serviço {{site.data.keyword.apiconnect_short}} configurado, ele o incluirá
automaticamente com um plano Lite grátis e migrará a API. Se sua instância falhou ao
provisionar, conclua as etapas em [Migrando manualmente as
APIs para {{site.data.keyword.apiconnect_short}}](#man_migrate_api) para migrá-la manualmente
para o novo serviço. 

6. Antes de fechar a tela da API original, desative a régua de controle para
**Expor API gerenciada**. Isso evita que alguém aja no terminal da versão antiga.

### Cloud Foundry API

1. Abra a origem da API do Cloud Foundry existente no painel do
{{site.data.keyword.Bluemix_notm}}. 

2. Selecione **Gerenciamento de API** no menu de navegação.

3. Selecione **Definição** na navegação.

4. Selecione **Arquivo de definição de API** > **Abrir no API Connect** > **Continuar**. Se
você já tiver um serviço {{site.data.keyword.apiconnect_short}} existente, ele
migrará automaticamente a API para o serviço existente. Se você ainda não tiver um
serviço {{site.data.keyword.apiconnect_short}} configurado, ele o incluirá
automaticamente com um plano Lite grátis e migrará a API. Se sua instância falhou ao
provisionar, conclua as etapas em [Migrando manualmente as
APIs para {{site.data.keyword.apiconnect_short}}](#man_migrate_api) para migrá-la manualmente
para o novo serviço.
   
5. Após o conteúdo ter sido migrado para a instância
{{site.data.keyword.apiconnect_short}}, selecione o link que é fornecido
para acessar a versão migrada.
    **Importante:** Para evitar problemas com várias instâncias da
API em execução, certifique-se de desativar a régua de controle *Gerenciar a
API* na versão original da API.

6. Selecione a guia **APIs** na navegação.

7. Selecione **Rascunhos** para visualizar sua nova API.

## Migrando APIs manualmente para {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

Se o processo para migrar sua API para o serviço
{{site.data.keyword.apiconnect_short}} não for concluído corretamente, conclua
as seguintes etapas para migrá-lo manualmente:

1. Abra sua API.
	1. Conecte-se ao {{site.data.keyword.Bluemix_notm}}.
	2. Para um aplicativo Cloud Foundry: 
		1. Selecione **Painel** no Menu.
		2. Selecione o nome do app Cloud Foundry que você deseja migrar.
		3. Selecione **API Management** na navegação.
	3. Para uma ação do Cloud Functions: 
		1. Selecione **Functions** no Menu.
		2. Selecione **APIs** na navegação.
		3. Selecione o nome da API que você deseja migrar.
2. Faça download do documento Swagger para a API por meio do gerenciamento de API.
    1. Selecione **Definição** na navegação.
	2. Selecione **Arquivo de definição de API**.
    3. Selecione **Exportar YAML** ou **Exportar
JSON**, dependendo de seu tipo de arquivo, para fazer download da definição da
API. O arquivo faz download para sua pasta de downloads.
3. Crie e prepare a instância do {{site.data.keyword.apiconnect_short}}. 
	1. Acesse **APIs** na navegação para filtrar os serviços.
	2. Selecione o serviço API Connect. 
    3. Crie uma instância do serviço do {{site.data.keyword.apiconnect_short}} por meio do catálogo do {{site.data.keyword.Bluemix_notm}}.
	4. Selecione seu plano. O plano Lite é a opção grátis.
	5. Selecione **Criar** para criar a instância.
4. Importe o documento Swagger para sua instância do {{site.data.keyword.apiconnect_short}} concluindo as etapas a seguir:
	1. No painel de serviço do {{site.data.keyword.apiconnect_short}}, selecione **Navegar para... (>>)** > **Rascunhos** no menu.
	2. Selecione a guia APIs.
	3. Selecione **+Incluir** > **Importar API por meio de um arquivo ou URL**.
	4. Localize e selecione o arquivo Swagger que você transferiu por download por meio do gerenciamento de API. Selecione **Abrir**.
	5. Selecione **Importar** para importar a API no serviço do {{site.data.keyword.apiconnect_short}}.
5. Para evitar problemas que resultam da execução de várias instâncias da API,
certifique-se de desativar a régua de controle *Gerenciar a API* na versão
original da API.

Sua API está disponível na instância de serviço.
{{site.data.keyword.apiconnect_short}} 

## Publicar a API

Você pode continuar a publicar a API concluindo as seguintes etapas:

1. Crie um catálogo.
	1. Selecione **+Incluir** para criar um catálogo.
	2. Insira um nome de exibição e um nome para seu catálogo e selecione **Incluir**.
	3. Selecione o catálogo que você criou.
2. Especifique as configurações para sua API.
    1. Selecione **Criar produto**.
	2. Especifique um nome para o produto.
	2. Selecione o produto que você criou para visualizar suas configurações.
	3. Configure o limite de taxa para a API.
	4. Configure a camada para a API.
3. Inclua o terminal para a API, se necessário.
    1. Selecione a API.
	2. Selecione a guia Montagem.
	3. Inclua o terminal, se ele ainda não estiver especificado.
	
 Depois de migrar suas APIs, você poderá acessar todos os recursos de gerenciamento
de API abrindo o quadro de serviços {{site.data.keyword.apiconnect_short}} e por
meio do painel do {{site.data.keyword.Bluemix_notm}}. 

