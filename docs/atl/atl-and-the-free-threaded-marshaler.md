---
title: ATL 和自由线程封送处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fa2e03bbb7307b2bc9633c21510f3b1939d4ad9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218043"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 和自由线程封送拆收器
ATL 简单对象向导的属性页提供了一个允许您的类聚合自由线程封送处理程序 (FTM) 选项。  
  
 该向导生成代码，以创建自由线程封送处理程序中的实例`FinalConstruct`和释放该实例中的`FinalRelease`。 COM_INTERFACE_ENTRY_AGGREGATE 宏自动添加到 COM 映射，以确保`QueryInterface`请求[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)自由线程封送处理程序处理。  
  
 自由线程封送处理程序允许直接访问你的对象的接口从在同一进程中任何线程加快跨单元调用。 此选项适用于使用这两个线程模型的类。  
  
 使用此选项时，类必须负责其数据的线程安全。 此外，聚合自由线程封送处理程序，并需要使用从其他对象中获得的接口指针的对象必须采取额外步骤来确保正确封送的接口。 这通常涉及将接口指针存储在全局接口表 (GIT)，使用它每次从 GIT 获取指针。 ATL 提供的类[CComGITPtr](../atl/reference/ccomgitptr-class.md)可帮助你使用存储在 GIT 中的接口指针。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)   
 [IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)   
 [何时使用全局接口表](/windows/desktop/com/when-to-use-the-global-interface-table)   
 [进程内服务器线程处理问题](/windows/desktop/com/in-process-server-threading-issues)

