---
title: "显式链接 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "显式链接 [C++]"
ms.assetid: 1e13d960-a195-4e6d-9864-7d8f3a701f4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 显式链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在显式链接下，应用程序必须进行函数调用以在运行时显式加载 DLL。  为显式链接到 DLL，应用程序必须：  
  
-   调用 **LoadLibrary**（或相似的函数）以加载 DLL 和获取模块句柄。  
  
-   调用 **GetProcAddress**，以获取指向应用程序要调用的每个导出函数的函数指针。  由于应用程序是通过指针调用 DLL 的函数，编译器不生成外部引用，故无需与导入库链接。  
  
-   使用完 DLL 后调用 **FreeLibrary**。  
  
 例如：  
  
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
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 您想进一步了解什么？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 请参阅  
 [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)