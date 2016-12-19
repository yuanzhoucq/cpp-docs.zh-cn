---
title: "加载时应使用哪些优化技术来提高客户端应用程序的性能？ | Microsoft Docs"
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
  - "DLL [C++], 优化"
  - "优化 [C++], DLL"
  - "性能 [C++], DLL"
ms.assetid: 2f8bbfb5-08b9-4a35-8302-25a1966881b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 加载时应使用哪些优化技术来提高客户端应用程序的性能？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果 DLL 是静态链接到 MFC 的规则 DLL，将它转换为动态链接到 MFC 的规则 DLL 会减小文件大小。  
  
 如果 DLL 具有大量导出函数，则使用 .def 文件导出函数，而不是使用 **\_\_declspec\(dllexport\)**，并在每个导出函数上使用 .def 文件 [NONAME 特性](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  NONAME 特性使得仅在 DLL 的导出表中存储序号值而不存储函数名，从而减小文件大小。  
  
 隐式链接到应用程序的 DLL 在程序加载时被加载。  若要提高加载时的性能，请试着将 DLL 分割为不同的 DLL。  将调用应用程序加载后立即需要的所有函数放在一个 DLL 中，并使调用应用程序隐式链接到该 DLL。  将调用应用程序当时不需要的其他函数放在另一个 DLL 中，并使应用程序显式链接到此 DLL。  有关更多信息，请参见[确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)。  
  
## 请参阅  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)