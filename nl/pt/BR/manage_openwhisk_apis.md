---

copyright:
  years: 2017,2018
lastupdated: "2018-01-11"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criar APIs por meio de ações do {{site.data.keyword.openwhisk_short}}
{: #manage_openwhisk_apis}

As ações do {{site.data.keyword.openwhisk_short}} podem se beneficiar pelo gerenciamento de API.

Com o gerenciamento de API, é possível expor uma ação do {{site.data.keyword.openwhisk_short}} como uma API. Depois de definir a API, é possível aplicar políticas de segurança e de limitação de taxa, visualizar o uso da API e os logs de resposta e definir políticas de compartilhamento de API.  

Para criar uma API do {{site.data.keyword.openwhisk_short}}, conclua as etapas a seguir:

1. No Painel do {{site.data.keyword.openwhisk_short}}, clique na guia **APIs**. Se você já tiver as APIs do {{site.data.keyword.openwhisk_short}} criadas, uma lista de suas APIs do {{site.data.keyword.openwhisk_short}} será exibida. Se você não tiver nenhuma API do {{site.data.keyword.openwhisk_short}}, uma tela de Introdução será exibida. 
2. Clique em **Criar uma API {{site.data.keyword.openwhisk_short}}**. A janela Criar API para {{site.data.keyword.openwhisk_short}} é exibida. 
3. Preencha os campos na seção Informações da API e, em seguida, clique em **Criar Operação**. A janela Criar Operação é exibida. Crie operações para definir o terminal, o caminho https e o método para sua API.
4. Na janela "Criar operação", preencha os campos necessários para sua operação do {{site.data.keyword.openwhisk_short}}. Entre os campos que são incluídos na janela "Criar operação" estão:

    * Caminho - o caminho para o local onde a API está localizada. 
    * Verbo - o método de HTTP para a API. Selecione nos métodos a seguir:
	    * DELETE
		* RECEBER
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* COLOCAR
	* Pacote que contém ação - os pacotes que já estão disponíveis em sua organização que podem ter a ação que deseja usar para essa API. Consulte [Usando e criando pacotes de funções Cloud](../openwhisk/openwhisk_packages.html) para obter informações adicionais sobre esse campo.
	* Ações - **ações que estão disponíveis no {{site.data.keyword.Bluemix_notm}}** são a única opção que está disponível.
	* Tipo de conteúdo de resposta - identifica o formato no qual a API retorna as informações. Você pode selecionar os seguintes formatos:
	    * application/json - esse é o formato padrão e é o mais usado.
		* text/html - é usado para respostas que são usadas em um website.
		* text/plain - é fornecido em texto simples e pode ser usado em arquivos de valores separados por vírgula.
		* image/svg+xml - pode ser usado quando capturas de tela são o formato principal das respostas.
		* Use o cabeçalho "Content-Type" da ação - é dependente do tipo de conteúdo que estiver no cabeçalho da resposta. 
	
5. Selecione **Criar** para criar a operação. A operação é incluída na tabela Operações que chamam ações do {{site.data.keyword.openwhisk_short}}.
5. Preencha as informações restantes que você deseja completar. Também é possível incluir ou atualizar as informações restantes posteriormente quando você gerencia suas APIs.
6. Clique em **Salvar**. A página de visão geral de gerenciamento de API para sua API se abre e todas as informações que você acabou de definir são exibidas.
7. Continue gerenciando sua API com [Gerenciar APIs](manage_apis.html).
