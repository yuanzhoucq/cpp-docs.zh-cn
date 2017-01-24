---
title: "ASP，ATL Active Server Page 组件向导 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.asp.asp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL Active Server Page 组件向导，ASP"
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ASP，ATL Active Server Page 组件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用“ATL Active Server Page 组件向导”的该页指定用于处理 ASP 组件的相关信息和状态的可选设置。  
  
 **可选方法**  
 向对象中添加可选 ASP 方法 **OnStartPage** 和 **OnEndPage**。  必须选定此选项才能设置任何 Active Server Page 内部对象。  默认情况下，此选项是选定的。  
  
-   **OnStartPage\/OnEndPage** 当脚本第一次尝试访问对象时调用 [OnStartPage](https://msdn.microsoft.com/en-us/library/ms691624.aspx)。  对象结束处理脚本时调用 **OnEndPage**。  
  
 **内部对象**  
 必须选定“OnStartPage\/OnEndPage”选项才能设置任何 ASP 内部对象。  
  
|选项|说明|  
|--------|--------|  
|**请求**|提供对 Active Server Page 内部 **Request** 对象的访问。  Request 对象用于传递 HTTP 请求。|  
|**响应**|提供对 Active Server Page 内部 **Response** 对象的访问。  为响应请求，Response 对象向浏览器发送信息以显示给用户。|  
|**会话**|提供对 Active Server Page 内部 **Session** 对象的访问。  **Session** 对象维护有关当前用户会话的信息，包括存储和检索状态信息。|  
|**Application**|提供对 Active Server Page 内部 **Application** 对象的访问。  **Application** 对象管理在多个 ASP 对象间共享的状态。|  
|**服务器**|提供对 Active Server Page 内部 **Server** 对象的访问。  **Server** 对象使您得以创建其他 ASP 对象。|  
  
## 请参阅  
 [ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)