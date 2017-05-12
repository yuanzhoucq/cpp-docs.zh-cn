---
title: "链接器工具错误 LNK1561 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: fbc63a58cd4e276aa2a3f77baeea07d1912eda98
ms.lasthandoff: 04/24/2017

---
# <a name="linker-tools-error-lnk1561"></a>链接器工具错误 LNK1561
必须定义入口点  
  
链接器找不到入口点。 此错误可以有几个原因︰  
-   你可能不包含要链接的文件列表中定义的入口点的文件。 验证该文件包含入口点函数已链接到你的应用。  
-   您可能定义了使用错误的函数签名中; 的入口点例如，你可能有拼写错误或用于错误的大小写的函数名称，或未正确指定返回类型或参数类型。 默认情况下，链接器查找`main`或`wmain`控制台应用程序，函数`WinMain`或`wWinMain`函数对于 Windows 应用，或`DllMain`需要初始化的 dll。  
-   你可能不指定[/DLL](../../build/reference/dll-build-a-dll.md)选项生成 DLL 时。  
-   你可能已指定入口点函数的名称不正确地在使用时[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。  
-   如果你使用[LIB](../../build/reference/lib-reference.md)工具来生成 DLL，你可能已指定.def 文件。 如果是这样，从生成中移除.def 文件。    
  
在生成应用程序，链接器将查找*入口点*，该函数调用以启动你的代码。 这是应用程序已加载并且在初始化运行时之后调用的函数。 必须提供一个应用程序入口点函数，或你的应用无法运行。 入口点是可选的 DLL。 默认情况下，链接器查找具有多个特定名称和签名，如是入口点函数`int main(int, char**)`。 你可以将另一个函数名称指定为该条目使用 /ENTRY 链接器选项的点。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```