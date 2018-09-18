---
title: ASP，ATL Active Server Page 组件向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.asp
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31ac9d8ab0200d8dd56bbca3c82eb0ebec32388b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015961"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP，ATL Active Server Page 组件向导

ATL Active Server Page 组件向导此页用于指定用于处理信息和状态与 ASP 组件相关的可选设置。

- **可选方法**  

   添加了可选的 ASP 方法， **onstartpage 是否**并**OnEndPage**，对你的对象。 若要设置任何 Active Server Pages 内部对象，必须选择此选项。 默认情况下，选择它。

- **Onstartpage / OnEndPage**

   [Onstartpage 是否](https://msdn.microsoft.com/library/ms691624.aspx)脚本会尝试访问该对象在首次调用。 **OnEndPage**对象完成时调用处理脚本。

- **内部对象**  

   必须选择**onstartpage 是否/OnEndPage**选项可以设置任何 ASP 内部对象。

|选项|描述|
|------------|-----------------|
|**请求**|提供对内部 Active Server Pages 的访问**请求**对象。 请求对象用于将 HTTP 请求传递。|
|**响应**|提供对内部 Active Server Pages 的访问**响应**对象。 在对请求的响应，则响应对象将信息发送到浏览器，以向用户显示。|
|**会话**|提供对内部 Active Server Pages 的访问**会话**对象。 **会话**对象维护有关当前用户会话，包括存储和检索状态信息的信息。|
|**应用程序**|提供对内部 Active Server Pages 的访问**应用程序**对象。 **应用程序**对象管理跨多个 ASP 对象共享的状态。|
|**服务器**|提供对内部 Active Server Pages 的访问**Server**对象。 **Server**对象使用户可以创建其他 ASP 对象。|

## <a name="see-also"></a>请参阅

[ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)

