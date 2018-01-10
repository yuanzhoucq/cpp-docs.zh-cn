---
title: "链接器工具错误 LNK1561 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1561
dev_langs: C++
helpviewer_keywords: LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cbd0ca9e932bdb2845ada2f47b569391e943cb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1561"></a>链接器工具错误 LNK1561
必须定义入口点  
  
找不到链接器*入口点*，要调用你的可执行文件中的初始函数。 默认情况下，链接器查找`main`或`wmain`控制台应用程序，函数`WinMain`或`wWinMain`函数对于 Windows 应用，或`DllMain`需要初始化的 dll。 你可以通过使用指定另一个函数[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。  
  
此错误可以有几个原因：  
-   你可能不包含要链接的文件列表中定义的入口点的文件。 验证该文件包含入口点函数已链接到你的应用。  
-   您可能定义了使用错误的函数签名中; 的入口点例如，你可能有拼写错误或用于错误的大小写的函数名称，或未正确指定返回类型或参数类型。  
-   你可能不指定[/DLL](../../build/reference/dll-build-a-dll.md)选项生成 DLL 时。  
-   你可能已指定入口点函数的名称不正确地在使用时[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。  
-   如果你使用[LIB](../../build/reference/lib-reference.md)工具来生成 DLL，你可能已指定.def 文件。 如果是这样，从生成中移除.def 文件。    
  
在生成应用程序，链接器将查找要调用以启动你的代码的入口点函数。 这是应用程序已加载并且在初始化运行时之后调用的函数。 必须提供一个应用程序入口点函数，或你的应用无法运行。 入口点是可选的 DLL。 默认情况下，链接器查找具有多个特定名称和签名，如是入口点函数`int main(int, char**)`。 你可以将另一个函数名称指定为该条目使用 /ENTRY 链接器选项的点。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```