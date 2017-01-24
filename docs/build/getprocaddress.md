---
title: "GetProcAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProcAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], GetProcAddress"
  - "GetProcAddress 方法"
  - "序号导出 [C++]"
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# GetProcAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

显式链接到 DLL 的进程调用 [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) 来获取 DLL 导出函数的地址。  使用返回的函数指针调用 DLL 函数。  **GetProcAddress** 将（由 **LoadLibrary**、`AfxLoadLibrary` 或 **GetModuleHandle** 返回的）DLL 模块句柄和要调用的函数名或函数的导出序号用作参数。  
  
 由于是通过指针调用 DLL 函数并且没有编译时类型检查，需确保函数的参数是正确的，以便不会超出在堆栈上分配的内存和不会导致访问冲突。  帮助提供类型安全的一种方法是查看导出函数的函数原型，并创建函数指针的匹配 typedef。  例如：  
  
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
  
 调用 **GetProcAddress** 时指定所需函数的方式取决于 DLL 的生成方式。  
  
 仅当要链接到的 DLL 是用模块定义 \(.def\) 文件生成的，并且序号在 DLL 的 .def 文件的 **EXPORTS** 部分中与函数一起列出时，才能获取导出序号。  如果 DLL 具有许多导出函数，则相对于使用函数名，使用导出序号调用 **GetProcAddress** 的速度稍快一些，因为导出序号是 DLL 导出表的索引。  使用导出序号，**GetProcAddress** 可直接定位函数，而不是将指定名称与 DLL 导出表中的函数名进行比较。  但是，仅当有权控制 .def 文件中导出函数的序号分配时，才应使用导出序号调用 **GetProcAddress**。  
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 您想进一步了解什么？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [\<caps:sentence id\="tgt17" sentenceid\="8c920606bb67e2587dd3c3e5cf977593" class\="tgtSentence"\>FreeLibrary\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [使用 DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)