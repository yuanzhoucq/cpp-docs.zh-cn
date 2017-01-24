---
title: "_SCL_SECURE_NO_WARNINGS | Microsoft Docs"
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
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _SCL_SECURE_NO_WARNINGS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用任何一个潜在的不安全的方法在标准 C\+\+ 库中的 [编译器警告（等级 3）C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  若要禁用此警告，请定义代码中宏 **\_SCL\_SECURE\_NO\_WARNINGS** :  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## 备注  
 其他方式禁用包含警告 C4996:  
  
-   使用 [\/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md) 编译器选项：  
  
    ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
    ```  
  
-   使用 [\/w](../build/reference/compiler-option-warning-level.md) 编译器选项：  
  
    ```  
    cl /wd4996 [other compiler options] myfile.cpp  
    ```  
  
-   使用 [\#pragma 警告](../preprocessor/warning.md) 指令：  
  
    ```  
    #pragma warning(disable:4996)  
    ```  
  
 此外，还可以手动更改标准警告带编译器选项 **\/w\<l\>\<n\>** 的 C4996。  例如，将警告 C4996 到 4 级：  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 有关详细信息，请参阅[\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../build/reference/compiler-option-warning-level.md)。  
  
## 请参阅  
 [安全库：C\+\+ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)