---
title: "导入函数调用使用 __declspec （dllimport） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5553bd5e9999a4737dc258358402eb71269b9c40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="importing-function-calls-using-declspecdllimport"></a>使用 __declspec(dllimport) 导入函数调用
下面的代码示例演示如何使用**_declspec(dllimport)**若要将函数调用从 DLL 导入到应用程序。 假定`func1`是驻留在单独的.exe 文件中包含的 DLL 函数**主要**函数。  
  
 而无需**__declspec （dllimport)**，给定此代码：  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 编译器生成的代码如下所示：  
  
```  
call func1  
```  
  
 和链接器会将转换到类似于以下调用：  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 如果`func1`中存在另一个 DLL，链接器无法直接解决因为它具有无法知道哪些的地址`func1`是。 在 16 位环境中，链接器将此代码地址添加到中加载程序将修补程序在运行时带有正确的地址的.exe 文件的列表。 在 32 位和 64 位环境中，链接器生成一个 thunk，其中它知道其地址。 在 32 位环境中转换 （thunk） 如下所示：  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 此处`imp_func1`的地址是`func1`.exe 文件的导入地址表中的槽。 链接器就知道所有地址。 仅加载程序必须在加载时，所有操作都要正确更新.exe 文件的导入地址表。  
  
 因此，使用**__declspec （dllimport)**比较好，因为链接器不会生成一个 thunk，如果不需要。 Thunk 使代码更大 （RISC 在系统上，它可以是几种指令），会降低缓存性能。 如果指示编译器在 DLL 中的功能，它可以为你生成的间接调用。  
  
 因此，现在此代码：  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 生成此指令：  
  
```  
call DWORD PTR __imp_func1  
```  
  
 没有任何转换 （thunk），但未`jmp`指令，因此的代码为更小、 更快。  
  
 另一方面，针对 DLL 内部的函数调用，您不想要必须使用间接调用。 你已经知道函数的地址。 因为需要时间和空间以加载和存储间接调用之前函数的地址，直接调用始终是更快、 更小。 你只想要使用**__declspec （dllimport)**调用 DLL 函数从外部 DLL 本身时。 不要使用**__declspec （dllimport)** DLL 时生成该 DLL 内部的函数。  
  
## <a name="see-also"></a>请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)