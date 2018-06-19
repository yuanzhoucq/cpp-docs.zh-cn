---
title: 使用 IDispEventImpl (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 520d1129234a26ff6eb4c402154969ad7e166211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361146"
---
# <a name="using-idispeventimpl"></a>使用 IDispEventImpl
使用时`IDispEventImpl`来处理事件，你将需要：  
  
-   派生您的类从[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
-   将事件接收器映射添加到你的类。  
  
-   将条目添加到事件接收器映射使用[SINK_ENTRY](reference/composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)宏。  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]  
  
 下面的代码将显示在 NotSoSimple.h。 通过注释记录了相关的代码：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]  
  
## <a name="see-also"></a>请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 示例](../visual-cpp-samples.md)

