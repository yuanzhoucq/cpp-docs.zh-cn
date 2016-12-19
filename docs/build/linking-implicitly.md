---
title: "隐式链接 | Microsoft Docs"
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
  - "隐式链接 [C++]"
  - "加载时动态链接 [C++]"
  - "静态加载链接 [C++]"
ms.assetid: 3ea4c316-4e70-4111-9944-c1b4ad00c605
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 隐式链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为隐式链接到 DLL，可执行文件必须从 DLL 的提供程序获取下列各项：  
  
-   包含导出函数和\/或 C\+\+ 类的声明的头文件（.h 文件）。类、函数和数据均应具有 `__declspec(dllimport)`，有关更多信息，请参见 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。  
  
-   要链接的导入库（[.LIB files](../build/reference/dot-lib-files-as-linker-input.md)）。（生成 DLL 时链接器创建导入库。）  
  
-   实际的 DLL（.dll 文件）。  
  
 使用 DLL 的可执行文件必须包括头文件，此头文件包含每个源文件中的导出函数（或 C\+\+ 类），而这些源文件包含对导出函数的调用。  从编码的角度讲，导出函数的函数调用与任何其他函数调用一样。  
  
 若要生成调用可执行文件，必须与导入库链接。  如果使用的是外部生成文件，请指定导入库的文件名，此导入库中列出了要链接到的其他对象 \(.obj\) 文件或库。  
  
 操作系统在加载调用可执行文件时，必须能够定位 DLL 文件。  
  
## 你希望做什么？  
  
-   [显式链接](../build/linking-explicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 您想进一步了解什么？  
  
-   [处理导入库和导出文件](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 请参阅  
 [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)