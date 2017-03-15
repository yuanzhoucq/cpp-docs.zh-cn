---
title: "strict_gs_check | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "strict_gs_check"
  - "strict_gs_check_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strict_gs_check 杂注"
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# strict_gs_check
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此杂注提供了增强的安全检查。  
  
## 语法  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## 备注  
 指示编译器在函数堆栈中插入随机 Cookie 以帮助检测基于堆栈的缓冲区溢出的某些类别。  默认情况下，\/GS（缓冲区安全检查）编译器选项不会为所有函数插入 Cookie。  有关详细信息，请参阅 [\/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)。  
  
 您必须使用 \/GS（缓冲区安全检查）进行编译才能启用 strict\_gs\_check。  
  
 请在公开给可能有害的数据的代码模块中使用此杂注。  此杂注攻击性非常强，应用于可能不需要此防御的函数，但它为了最大程度降低其对生成的应用程序的性能的影响而进行优化。  
  
 即使您使用此杂注，也应尽可能写入安全的代码。  即，确保您的代码没有缓冲区溢出。strict\_gs\_check 可保护您的应用程序不发生确实保留在代码中的缓冲区溢出。  
  
## 示例  
 在以下代码中，缓冲区溢出出现在我们将数组复制到本地数组时。  使用 \/GS 编译此代码时，不会在堆栈中插入任何 Cookie，因为数组数据类型为指针。  添加 strict\_gs\_check 杂注会将堆栈 Cookie 强制插入函数堆栈。  
  
```cpp  
// pragma_strict_gs_check.cpp  
// compile with: /c  
  
#pragma strict_gs_check(on)  
  
void ** ReverseArray(void **pData,  
                     size_t cData)  
{  
    // *** This buffer is subject to being overrun!! ***  
    void *pReversed[20];  
  
    // Reverse the array into a temporary buffer  
    for (size_t j = 0, i = cData; i ; --i, ++j)  
        // *** Possible buffer overrun!! ***  
            pReversed[j] = pData[i];   
  
    // Copy temporary buffer back into input/output buffer  
    for (size_t i = 0; i < cData ; ++i)   
        pData[i] = pReversed[i];  
  
    return pData;  
}  
  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [\/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)