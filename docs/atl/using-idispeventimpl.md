---
title: 使用 IDispEventImpl (ATL) |Microsoft Docs
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
ms.openlocfilehash: 38ac64a99c3523f174c62c9788aeab867aa8758b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848923"
---
# <a name="using-idispeventimpl"></a>使用 IDispEventImpl
当使用`IDispEventImpl`来处理事件，你将需要：  
  
-   从类派生[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
-   将事件接收器映射添加到您的类。  
  
-   将条目添加到使用事件接收器映射[SINK_ENTRY](reference/composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)宏。  
  
-   实现你感兴趣处理的方法。  
  
-   通知和取消通知事件源。  
  
## <a name="example"></a>示例  
 下面的示例演示如何处理`DocumentChange`由 Word 的事件触发**应用程序**对象。 此事件指一种方法上`ApplicationEvents`调度接口。  
  
 该示例摘自[ATLEventHandling 示例](../visual-cpp-samples.md)。  
  
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
  
 该示例使用`#import`从 Word 的类型库生成必需的标头文件。 如果你想要使用此示例与其他版本的 Word，则必须指定正确 mso dll 文件。 例如，Office 2000 提供 mso9.dll 并 OfficeXP 提供 mso.dll 有关的问题。 此代码从 stdafx.h 简化：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]  
  
 下面的代码所示 NotSoSimple.h。 通过注释记录了相关代码：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]  
  
## <a name="see-also"></a>请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 示例](../visual-cpp-samples.md)

