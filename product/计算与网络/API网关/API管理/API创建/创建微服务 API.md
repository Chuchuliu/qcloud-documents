用户在进入服务后，可根据后端业务类型选择创建通用 API 或微服务 API，当后端业务实现在 TSF 中时，选择微服务 API 类型 tab，并单击新建：
![](https://main.qcloudimg.com/raw/914798c521505d7350fa2282bc75ecb8.png)

## 前端配置

如图所示，配置微服务 API 的前端配置，需要选择后端所对接微服务的集群、命名空间、及微服务。API 发布者可在一个 API 中对接多个微服务。

**HTTP 方法**：可选择 GET、POST、PUT、DELETE、PATCH、HEAD 方法。

**URL 路径（Path）**：您可以按需求写入合法 URL 路径。如需要在路径中配置动态参数，请使用 `{}` 符号，并在其中填入参数名，例如 `/user/{userid}` 路径，申明了路径中的 userid 参数，此参数同时需要在入参中作为 Path 类型参数进行定义。Query 参数可以不用在 URL 路径中定义。

**入参**：入参包含了来源于 Header、Query、Path 的参数。其中 Path 参数对应于在 URL 路径中定义的动态参数。任一参数，均需要指定参数名，参数类型和参数数据类型；同时可以指明是否必填、默认值、示例数据和描述说明。利用这些配置，API 网关可以协助您完成入参的文档化和初步校验。同时，可根据需要，在参数上加入更多更详细验证配置，例如最大最小值、最大最小长度、枚举值、甚至正则表达式。
在调用时需要传入两个必选参数：X-NameSpace-Code、X-MicroService-Name来告诉API网关这个请求是发往哪个微服务。这两个参数可放置在 header、path、query 中，若放在 path 中，则与通用 API 类似，需要在路径中配置路径参数。除了这两个固定参数。其他参数配置均与通用 API 一致。
![](https://main.qcloudimg.com/raw/58d61ef247203e8826943b0f965b476b.png)

## 后端配置

**后端请求路径**：具体的后端服务请求路径。如果需要在路径中配置动态参数，请使用`{}` 符号，并在其中填入参数名，此参数名将用于在参数映射的配置中配置为来源于前端配置的入参。这里的路径可与前端不同，做路径映射。为真正服务的请求路径。

**超时时间**：在 API 网关发起到后端服务调用的超时时间。超时时间的最大限制为 30 秒。在 API 网关调用后端服务，未在超时时间内获得响应时，API 网关将终止此次调用，并返回相应的错误信息。

**后端参数**：X-NameSpace-Code、X-MicroService-Name这两个参数为固定参数，不可做映射，用户配置的其他参数均可做映射。

**映射参数：**参数映射用于将前端的入参映射为实际后端服务的参数。映射参数默认会将入参以相同名字和参数位置进行映射。同时，您可以根据需求，变更参数的映射方式，例如将来源于 Path 的入参，映射为后端服务中 Query 参数。

**映射参数：**您可以根据需要，加入自行定义的常量参数。常量参数在每次 API 调用中都保持不变。同时，您可以利用系统参数，将所需的部分系统信息，传递给后端服务。

**映射参数：**如果您的body参数仅有表单格式，则可直接在前后端参数配置时映射。若为 json 格式，则 json 参数 API 网关会直接透传。

![](https://main.qcloudimg.com/raw/84b525b8b150995def8c2b64cb3489ad.png)

## 响应结果

API 响应配置包括 API 响应数据配置和 API 错误码配置。
API 响应数据配置，用于指明返回数据类型，包括成功调用的数据示例和失败调用的数据示例。
API 的错误码定义，用于指明额外的错误码，错误信息和描述。
![](https://main.qcloudimg.com/raw/edcbca70d8c41ab625fdac18cda9c8f4.png)
响应结果配置仅用于生成文档使用。


