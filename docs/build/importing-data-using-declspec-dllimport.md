---
title: "使用 __declspec(dllimport) 导入数据 | Microsoft Docs"
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
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 关键字 [C++]"
  - "dllimport 特性 [C++], 数据导入"
  - "导入数据 [C++]"
  - "导入 DLL [C++], __declspec(dllimport)"
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 __declspec(dllimport) 导入数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

就数据而言，使用 **\_\_declspec\(dllimport\)** 是移除间接层的方便手段。  从 DLL 导入数据时，仍需要仔细检查导入地址表。  在 **\_\_declspec\(dllimport\)** 之前，这意味着在访问从 DLL 导出的数据时必须记住进行额外的间接寻址：  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 然后导出 .DEF 文件中的数据：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 并从 DLL 外部访问这些数据：  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 将数据标记为 **\_\_declspec\(dllimport\)** 时，编译器自动为您生成间接代码。  您不必再为上述步骤操心了。  如前所述，生成 DLL 时不要在数据上使用 **\_\_declspec\(dllimport\)** 声明。  DLL 内部的函数不使用导入地址表访问数据对象；因此，不会再有额外的间接寻址了。  
  
 若要自动从 DLL 导出数据，请使用此声明：  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## 请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)