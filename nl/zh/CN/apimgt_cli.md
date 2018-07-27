---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Bluemix API Management 命令
{: #apimgt_cli}

版本：1.0.0

您可以安装 {{site.data.keyword.Bluemix_notm}} API Management 命令行界面 (CLI) 插件，以使用脚本完成对 API 的常见管理操作。以下信息列出了 API Management CLI 插件随附的命令，包括命令名称、选项、用法、先决条件、描述和示例。
{:shortdesc}

**注：****先决条件**列出使用命令前必须执行的操作。没有先决条件操作的命令会列出**无**。否则，先决条件可能会包含以下一个或多个操作：

**注：**您可以使用短格式的 bluemix 命令；例如，`bx apim` 是 `bluemix apim` 的短格式。

使用下表中的索引来参考经常使用的 API Management 命令。

<table summary="API Management 命令。">
<caption>表 1. API Management 命令</caption>
 <thead>
 <th colspan="5">API Management 命令</th>
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
 
  
## API Management 帮助
{: #apim_help}
显示 API Management CLI 的一级内置命令和受支持名称空间的一般帮助，或显示特定内置命令或名称空间的帮助。

### 语法

```
bluemix apim help <object-action>
```
{: codeblock}

### 命令选项

   <dl>
   <dt>object-action（可选）</dt>
   <dd>要显示其帮助的命令。如果未指定，将显示 API Management CLI 的一般帮助。</dd>
   </dl>

### 示例

显示 API Management CLI 的一般帮助：

```
bluemix apim help
```

显示 `api-create` 命令的帮助：

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
显示受管 API 的属性。

### 语法
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### 必需的标志
   <dl>
   <dt>--name</dt>
   <dd>指定受管 API 的名称</dd>
   </dl>


### 命令选项
   <dl>
   <dt>--swagger</dt>
   <dd>在输出中显示 Open API 定义文档中的信息</dd>
   </dl>

### 输出

此命令输出一个表，其中列出有关指定 API 的以下信息：

   <dl>
     <dt>名称</dt>
	 <dd>API 的名称。</dd>
	 <dt>类型</dt>
	 <dd>API 的类型。有效条目为 <em>whisk</em>、<em>cf-apps</em> 或 <em>user-defined</em></dd>
	 <dt>受管</dt>
	 <dd>如果值为 true，指示端点已发现但未在网关上公开。</dd>
	 <dt>已公开</dt>
	 <dd>指示 API 在网关上是处于活动状态 (<em>true</em>) 还是不活动状态 (<em>false</em>)。
	 <dt>共享</dt>
	 <dd>指示 API 是在 Bluemix 组织外部共享 (<em>true</em>) 还是不在 Bluemix 组织外部共享 (<em>false</em>)。</dd>
	 <dt>受管 URL</dt>
	 <dd>指定共享版本 API 的位置。</dd>
   </dl>

   
### 示例

显示名为 cloudfound1 的 API 的属性：

```
bluemix apim api cloudfound1
```

显示名为 api2 的 API 的属性和定义文件内容：

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


列出在已识别端点服务器上可用且识别到的 API。

### 语法
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### 命令选项

注：如果没有指定选项，将返回所有 API 的信息。
   <dl>
   <dt>--api-provider</dt>
   <dd>仅返回您在此处指定的 API 类型。有效选项为 <em>whisk</em>（对于 Openwhisk API）、<em>cf-apps</em>（对于 Cloud Foundry 应用程序 API）和 <em>user-defined</em>（对于未与 Openwhisk 或 Cloud Foundry 关联的 API）。</dd>
   <dt>--exposed</dt>
   <dd>仅返回公开的 API。</dd>
   <dt>--shared</dt>
   <dd>仅返回在 {{site.data.keyword.Bluemix_notm}} 组织外部共享的 API。</dd>
   </dl>

### 输出

此命令输出一个表，其中列出有关指定 API 的以下信息：

   <dl>
     <dt>名称</dt>
	 <dd>API 的名称。</dd>
	 <dt>类型</dt>
	 <dd>API 的类型。有效条目为 <em>whisk</em>、<em>cf-apps</em> 或 <em>user-defined</em></dd>
	 <dt>受管</dt>
	 <dd>如果值为 true，指示端点已发现但未在网关上公开。</dd>
	 <dt>已公开</dt>
	 <dd>指示 API 在网关上是处于活动状态 (<em>true</em>) 还是不活动状态 (<em>false</em>)。
	 <dt>共享</dt>
	 <dd>指示 API 是在 Bluemix 组织外部共享 (<em>true</em>) 还是不在 Bluemix 组织外部共享 (<em>false</em>)。</dd>
	 <dt>受管 URL</dt>
	 <dd>如果公开了共享版本 API，指定该 API 的位置。API 未公开时，值为 <em>undefined</em>。</dd>
   </dl>


### 示例

返回端点管理器上可用的所有 API：

```
bluemix apim apis 
```

返回可用的所有 OpenWhisk API：

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


通过导入其 Swagger 文件，将现有的非受管 API 变为受管 API。

### 语法

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要管理的 API 的名称。</dd>
   <dt>--file</dt>
   <dd>提供 YAML 或 JSON 格式的 Open API 定义文件的路径。</dd>
   <dt>--provider</dt>
   <dd>指定要创建的 API 的类型。注：此标志唯一有效的条目是 <em>cf-apps</em>。
   </dl>

### 命令选项

   <dl>
   <dt>--expose</dt>
   <dd>创建端点后自动将其公开。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功创建
* 错误（包含错误描述）

### 示例

管理名为 apinumber1 的 Cloud Foundry API，该 API 具有名为 reservations1 的 yaml 定义文件：

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

管理名为 cfapi 的 Cloud Foundry 应用程序，该应用程序具有名为 definition1 的 JSON 定义文件：

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

从数据库中除去受管 API。

### 语法

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要删除的 API 的名称。**重要信息：**删除 Cloud Foundry API 会将该 API 从受管状态中除去，但不会删除 Cloud Foundry 应用程序。删除 OpenWhisk API 将删除整个 API，并且必须在删除后加以重新创建。</dd>
   <dt>--confirm</dt>
   <dd>确认命令应该在没有提供确认提示的情况下完成。</dd>
   </dl>


### 输出

此命令输出以下信息：
* 已成功删除
* 错误（包含错误描述）

### 示例

删除 Cloud Foundry API cloudapi1：

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

使受管 API 可供 {{site.data.keyword.Bluemix_notm}} 组织内部的其他人查看。

### 语法
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要公开的 API 的名称。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功公开
* 错误（包含错误描述）

### 示例

在 {{site.data.keyword.Bluemix_notm}} 组织中公开名为 cloudfound1 的 Cloud Foundry API：

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


使受管 API 可供 {{site.data.keyword.Bluemix_notm}} 组织外部的其他人查看。

### 语法
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要共享的 API 的名称。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功共享
* 错误（包含错误描述）

### 示例

在 {{site.data.keyword.Bluemix_notm}} 组织外部共享名为 cloudfound1 的 Cloud Foundry API：
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


使可供 {{site.data.keyword.Bluemix_notm}} 组织内部其他人查看的受管 API 不再可供其他人查看。

### 语法
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要禁止 {{site.data.keyword.Bluemix_notm}} 组织中其他人查看的 API 的名称。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功取消公开
* 错误（包含错误描述）

### 示例

禁止 {{site.data.keyword.Bluemix_notm}} 组织中其他成员查看名为 openwhisk1 的 OpenWhisk API：

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


使可供 {{site.data.keyword.Bluemix_notm}} 组织外部其他人查看的某个受管 API 不再可供查看。

### 语法
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>必需的标志</strong>：

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要停止共享的 API 的名称。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功取消共享
* 错误（包含错误描述）

### 示例

在 {{site.data.keyword.Bluemix_notm}} 组织外部停止共享名为 cloudfound1 的 Cloud Foundry API：

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


通过替换受管 API 的定义文件来更新其设置。重要信息：这将使用新文件中的定义完全替换该 API 中的现有定义。现有文件中存在而新文件中为空白或缺失的任何条目都将从定义中除去。

### 语法
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>指定要更新的 API 的名称。</dd>
   <dt>--file</dt>
   <dd>提供 YAML 或 JSON 格式的替换 Open API 定义文件的路径。</dd>
   </dl>

### 输出

此命令输出以下信息：
* 已成功更新
* 错误（包含错误描述）


### 示例

使用名为 definition1.json 的定义文件更新名为 whiskapi1 的 OpenWhisk API：

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


显示与受管 API 关联的密钥的属性。

### 语法
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### 必需的标志

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>指定要公开的 API 的名称。</dd>
   <dt>--bluemix</dt>
   <dd>列出指定 API 的 {{site.data.keyword.Bluemix_notm}} API 密钥。</dd>
   <dt>--external</dt>
   <dd>列出指定 API 的外部 API 密钥。</dd>
   </dl>

### 输出

此命令输出一个表，其中列出有关指定 API 的以下信息：


   <dl>
     <dt>密钥名称</dt>
	 <dd>API 密钥的名称。</dd>
	 <dt>密钥类型</dt>
	 <dd>API 密钥的类型。有效条目为 <em>bluemix</em> 和 <em>external</em>。</dd>
	 <dt>客户机标识</dt>
	 <dd>使用密钥识别的客户机的名称。</dd>
	 <dt>已提供私钥</dt>
	 <dd>指示是否为 API 提供了 API 私钥。可能的值为 <em>true</em>（如果有私钥）和 <em>false</em>（如果没有私钥）。
   </dl>


### 示例

返回与名为 cloudfound1 的 API 关联的所有外部密钥。

```
bluemix apim --name cloudfound1 --external
```

返回允许 {{site.data.keyword.Bluemix_notm}} 组织内部人员看到名为 myapi1 的 API 的密钥。

```
bluemix apim --name myapi1 --bluemix 
```
 
