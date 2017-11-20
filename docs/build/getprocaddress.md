---
title: "GetProcAddress |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GetProcAddress
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 426a0c5a40f3be3effdf4ba8316f6a72a8295965
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="getprocaddress"></a>GetProcAddress
显式链接到 DLL 调用的进程[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)获取 DLL 中导出的函数的地址。 使用返回的函数指针调用 DLL 函数。 **GetProcAddress**使用作为参数的 DLL 模块句柄 (通过以下任一方法返回**LoadLibrary**， `AfxLoadLibrary`，或**GetModuleHandle**) 将函数名称和你要调用或函数的导出序号。  
  
 由于要调用的 DLL 函数通过指针并且没有任何编译时类型检查，请确保函数的参数正确，以便不超出在堆栈上分配的内存，并且会导致访问冲突。 帮助提供类型安全的一种方法是查看导出的函数的函数原型，并创建匹配的函数指针的 typedef。 例如:   
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 如何指定所需时调用的函数**GetProcAddress**取决于 DLL 如何生成。  
  
 如果使用的模块定义 (.def) 文件生成要链接到 DLL，并列出中的函数的序号，仅可以获取导出序号**导出**DLL 的.def 文件的部分。 调用**GetProcAddress**与导出序号，而不是函数名称，是 DLL 具有许多导出的函数，因为索引到该 DLL 导出表作为导出序号稍微快一些。 与导出序号， **GetProcAddress**可以找到而比较指定的名称与 DLL 的导出表中的函数名称不是直接函数。 但是，你应调用**GetProcAddress**与仅当将序号分配到.def 文件中导出的函数的控制导出序号。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [如何将隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [使用 DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>另请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)