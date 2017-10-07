---
title: "进程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d4f2500adaaa7941444b22d7ce548370fc370533
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="process"></a>进程
指定托管应用程序进程在该过程中应具有特定全局变量、静态成员变量或在任何应用程序域之间共享的静态局部变量的单一副本。 这主要为了使用编译时使用**/clr： 纯**，这是因为下**/clr: pure**全局和静态变量是每个应用程序域，默认情况下。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。 使用编译时**/clr**，全局和静态变量是每个进程默认情况下 (不需要使用`__declspec(process)`。  
  
 只有本机类型的全局变量、静态成员变量或静态局部变量可以使用 `__declspec(process)` 标记。  
  
 使用编译时**/clr: pure**，还必须将标记每个进程的变量声明为`const`。 这可确保每个进程变量在一个应用程序域中不会改变，并且不会在其他应用程序域中生成意外的结果。 主要用途的`__declspec(process)`是启用全局变量、 静态成员变量或在静态局部变量的编译时初始化**/clr: pure**。  
  
 `process`使用编译时才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)或**/clr: pure**和编译时不有效**/clr: safe**。  
  
 如果你希望每个应用程序域具有其自己的全局变量副本，使用[appdomain](../cpp/appdomain.md)。  
  
 请参阅[应用程序域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)有关详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)
