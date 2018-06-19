---
title: 使用 IDispEventSimpleImpl (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cdef5012288b7f5f17040f73dfac5ec1f90d4f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361933"
---
# <a name="using-idispeventsimpleimpl"></a>使用 IDispEventSimpleImpl
使用时`IDispEventSimpleImpl`来处理事件，你将需要：  
  
-   派生您的类从[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)。  
  
-   将事件接收器映射添加到你的类。  
  
-   定义[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)结构描述的事件。  
  
-   将条目添加到事件接收器映射使用[SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)宏。  
  
-   实现你感兴趣处理的方法。  
  
-   通知和取消通知的事件源。  
  
## <a name="example"></a>示例  
 下面的示例演示如何处理**DocumentChange**由 Word 的激发的事件**应用程序**对象。 此事件指一种方法上**ApplicationEvents**调度接口。  
  
 此示例摘自[ATLEventHandling 示例](../visual-cpp-samples.md)。  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 该示例使用`#import`从 Word 的类型库生成必需的标头文件。 如果你想要使用此示例与其他版本的 Word，则必须指定正确的 mso dll 文件。 例如，Office 2000 提供 mso9.dll 并 OfficeXP 提供 mso.dll。 此代码是从 stdafx.h 简化了：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 此示例中实际使用的类型库中的唯一信息是单词的 CLSID**应用程序**对象和接口的 IID **ApplicationEvents**接口。 仅在编译时使用此信息。  
  
 下面的代码将显示在 Simple.h。 通过注释记录了相关的代码：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 下面的代码是从 Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 示例](../visual-cpp-samples.md)

