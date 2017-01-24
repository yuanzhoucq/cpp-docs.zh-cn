---
title: "CUrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CUrl"
  - "CUrl"
  - "ATL::CUrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUrl class"
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示URL。  它是否可以独立于其他操作URL的每个元素分析现有的URL字符串或从头开始生成字符串。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CUrl  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CUrl::CUrl](../Topic/CUrl::CUrl.md)|构造函数。|  
|[CUrl::~CUrl](../Topic/CUrl::~CUrl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CUrl::Canonicalize](../Topic/CUrl::Canonicalize.md)|调用此方法将URL字符串转换为规范格式。|  
|[CUrl::Clear](../Topic/CUrl::Clear.md)|调用此方法清除任何URL字段。|  
|[CUrl::CrackUrl](../Topic/CUrl::CrackUrl.md)|调用此方法对和分析URL。|  
|[CUrl::CreateUrl](../Topic/CUrl::CreateUrl.md)|调用此方法创建URL。|  
|[CUrl::GetExtraInfo](../Topic/CUrl::GetExtraInfo.md)|调用此方法获取附加信息\(例如?*文本* 或\#text\)从URL。|  
|[CUrl::GetExtraInfoLength](../Topic/CUrl::GetExtraInfoLength.md)|调用此方法获取附加信息的长度\(例如? \)检索的*文本* 或\#text从URL。|  
|[CUrl::GetHostName](../Topic/CUrl::GetHostName.md)|调用此方法获取URL中的主机名。|  
|[CUrl::GetHostNameLength](../Topic/CUrl::GetHostNameLength.md)|调用此方法获取主机名的长度。|  
|[CUrl::GetPassword](../Topic/CUrl::GetPassword.md)|调用此方法获取URL的密码。|  
|[CUrl::GetPasswordLength](../Topic/CUrl::GetPasswordLength.md)|调用此方法获取密码的长度。|  
|[CUrl::GetPortNumber](../Topic/CUrl::GetPortNumber.md)|调用此方法获取端口号基于ATL\_URL\_PORT。|  
|[CUrl::GetScheme](../Topic/CUrl::GetScheme.md)|调用此方法获取URL模式。|  
|[CUrl::GetSchemeName](../Topic/CUrl::GetSchemeName.md)|调用此方法获取URL模式名称。|  
|[CUrl::GetSchemeNameLength](../Topic/CUrl::GetSchemeNameLength.md)|调用此方法获取URL模式名称的长度。|  
|[CUrl::GetUrlLength](../Topic/CUrl::GetUrlLength.md)|调用此方法获取URL长度。|  
|[CUrl::GetUrlPath](../Topic/CUrl::GetUrlPath.md)|调用此方法获取URL路径。|  
|[CUrl::GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md)|调用此方法获取URL路径长度。|  
|[CUrl::GetUserName](../Topic/CUrl::GetUserName.md)|调用此方法获取URL的用户名。|  
|[CUrl::GetUserNameLength](../Topic/CUrl::GetUserNameLength.md)|调用此方法获取用户名的长度。|  
|[CUrl::SetExtraInfo](../Topic/CUrl::SetExtraInfo.md)|调用此方法设置附加信息\(例如?*文本* 或\#text\) URL。|  
|[CUrl::SetHostName](../Topic/CUrl::SetHostName.md)|调用此方法设置主机名。|  
|[CUrl::SetPassword](../Topic/CUrl::SetPassword.md)|调用此方法设置密码。|  
|[CUrl::SetPortNumber](../Topic/CUrl::SetPortNumber.md)|调用此方法将端口号基于ATL\_URL\_PORT。|  
|[CUrl::SetScheme](../Topic/CUrl::SetScheme.md)|调用此方法设置URL模式。|  
|[CUrl::SetSchemeName](../Topic/CUrl::SetSchemeName.md)|调用此方法设置URL模式名称。|  
|[CUrl::SetUrlPath](../Topic/CUrl::SetUrlPath.md)|调用此方法设置URL路径。|  
|[CUrl::SetUserName](../Topic/CUrl::SetUserName.md)|调用此方法设置用户名。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CUrl::operator \=](../Topic/CUrl::operator%20=.md)|分配给当前 `CUrl` 对象的指定 `CUrl` 对象。|  
  
## 备注  
 `CUrl` 使您可以操作一个URL字段，如路径或端口号。  `CUrl` 了解以下形式的URL:  
  
 \<Scheme\>: \/\<UserName\>:\<Password\>@\<HostName\>:\<PortNumber\>\/\<UrlPath\>\<ExtraInfo\>  
  
 （某些字段都是可选的。）例如，请考虑此URL:  
  
 http:\/\/someone:secret@www.microsoft.com:80\/visualc\/stuff.htm\#contents  
  
 [CUrl::CrackUrl](../Topic/CUrl::CrackUrl.md) 分析该如下所示:  
  
-   模式:“HTTP”或 [ATL\_URL\_SCHEME\_HTTP](../Topic/ATL_URL_SCHEME.md)  
  
-   用户名:“用户”  
  
-   password:“计算”  
  
-   主机名:“www.microsoft.com”  
  
-   PortNumber:80  
  
-   UrlPath:“visualc\/stuff.htm”  
  
-   ExtraInfo:“\#contents”  
  
 若要操作UrlPath字段\(如\)，则应使用 [GetUrlPath](../Topic/CUrl::GetUrlPath.md)、 [GetUrlPathLength](../Topic/CUrl::GetUrlPathLength.md)和 [SetUrlPath](../Topic/CUrl::SetUrlPath.md)。  您将使用 [CreateUrl](../Topic/CUrl::CreateUrl.md) 创建完整的URL字符串。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [类](../../atl/reference/atl-classes.md)