---
title: "ATL 和自由线程封送处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed5660be9a5559d5f51d0cdb0ec2e5bc185bd0b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 和自由线程封送拆收器
ATL 简单对象向导的属性页提供了一个允许你的类以聚合自由线程封送处理程序 (FTM) 的选项。  
  
 向导生成代码以创建自由线程封送处理程序中的一个实例`FinalConstruct`和释放该实例在`FinalRelease`。 A`COM_INTERFACE_ENTRY_AGGREGATE`宏自动添加到 COM 映射，以确保`QueryInterface`请求[IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)由自由线程封送处理程序。  
  
 自由线程封送处理程序允许直接访问你的对象的接口从任意线程在相同的过程中，加快跨单元调用。 此选项适用于使用这两个线程处理模型的类。  
  
 使用此选项时，类必须对负责其数据的线程安全性。 此外，聚合自由线程封送处理程序且需要使用从其他对象中获得的接口指针的对象必须采取额外步骤来确保接口正确封送。 这通常涉及到将接口指针存储在全局接口表 (GIT)，每次使用它时从 GIT 获取指针。 ATL 提供类[CComGITPtr](../atl/reference/ccomgitptr-class.md)以帮助你使用存储在 git 中获取的接口指针。  
  
## <a name="see-also"></a>另请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [何时使用全局接口表](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [进程内服务器线程处理问题](http://msdn.microsoft.com/library/windows/desktop/ms687205)

