---
title: "应用程序域和 Visual c + + |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a66731b9645458441f1c3e1f211c74be698e7231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="application-domains-and-visual-c"></a>应用程序域和 Visual C++
如果你有`__clrcall`虚拟函数，每个应用程序域 (appdomain) 将是 vtable。 如果在一个 appdomain 中创建的对象，只能调用在该 appdomain 中的虚拟函数。 在中定义的所有函数**/clr: pure**编译单位使用`__clrcall`调用约定。 因此，所有 vtable 中都定义了**/clr: pure**编译单位是每个 appdomain。 在混合模式下 (**/clr**) 如果你的类型未包含任何将具有每个进程 vtable`__clrcall`虚函数。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 有关详细信息，请参见  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [如何： 迁移到 /clr: pure (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [进程](../cpp/process.md)  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)