---
title: 避免由 COM 对象生成的 clr 与引发的异常 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 287c9831f8c604272b37ac85528d66fe640de557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>使用以 /clr 生成的 COM 对象时避免 CLR 关闭异常
公共语言运行时 (CLR) 进入后关闭模式，本机函数会限制对 CLR 服务的访问。 尝试对调用 Release COM 对象将编译使用**/clr**CLR 转换为本机代码，然后转换回为 iunknown:: Release 呼叫 （这在托管代码中定义） 提供服务的托管代码。 因为它处于关闭模式下，CLR 将阻止返回到托管代码调用。  
  
 若要解决此问题，请确保从 Release 方法调用的析构函数只能包含本机代码。  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)