---
title: "ASP，ATL Active Server Page 组件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.asp
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69d3837cc0996c0e0e0784214cfbfa6744afbf94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP，ATL Active Server Page 组件向导
使用 ATL Active Server Page 组件向导的此页指定用于处理信息和状态与 ASP 组件相关的可选设置。  
  
 **可选方法**  
 添加可选的 ASP 方法， **OnStartPage**和**OnEndPage**，对你的对象。 必须选择此选项设置任何 Active Server Pages 的内部对象。 默认情况下，选中该选项。  
  
-   **OnStartPage/OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx)称为第一次脚本尝试访问的对象。 **OnEndPage**对象完成时，将调用处理脚本。  
  
 **内部对象**  
 必须选择**OnStartPage/OnEndPage**选项可设置任何 ASP 内部对象。  
  
|选项|描述|  
|------------|-----------------|  
|**请求**|提供对内部 Active Server Pages 访问**请求**对象。 请求对象用于通过 HTTP 请求。|  
|**响应**|提供对内部 Active Server Pages 访问**响应**对象。 在对请求的响应，则响应对象将信息发送到浏览器将向用户显示。|  
|**会话**|提供对内部 Active Server Pages 访问**会话**对象。 **会话**对象维护有关当前用户会话，包括存储和检索状态信息的信息。|  
|**应用程序**|提供对内部 Active Server Pages 访问**应用程序**对象。 **应用程序**对象管理在多个 ASP 对象之间共享的状态。|  
|**服务器**|提供对内部 Active Server Pages 访问**服务器**对象。 **服务器**对象允许你创建其他 ASP 对象。|  
  
## <a name="see-also"></a>请参阅  
 [ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)

