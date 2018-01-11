---
title: "strict_gs_check |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs: C++
helpviewer_keywords: strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c355bd385a997e8ff3fd9ec323d50bb33b9c6fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strictgscheck"></a>strict_gs_check
此杂注提供了增强的安全检查。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## <a name="remarks"></a>备注  
 指示编译器在函数堆栈中插入随机 Cookie 以帮助检测基于堆栈的缓冲区溢出的某些类别。 默认情况下，/GS（缓冲区安全检查）编译器选项不会为所有函数插入 Cookie。 有关详细信息，请参阅 [/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)。  
  
 您必须使用 /GS（缓冲区安全检查）进行编译才能启用 strict_gs_check。  
  
 请在公开给可能有害的数据的代码模块中使用此杂注。 此杂注攻击性非常强，应用于可能不需要此防御的函数，但它为了最大程度降低其对生成的应用程序的性能的影响而进行优化。  
  
 即使您使用此杂注，也应尽可能写入安全的代码。 也就是说，请确保你的代码具有没有缓冲区溢出。 strict_gs_check 可能从你的代码中仍存在的缓冲区溢出保护你的应用程序。  
  
## <a name="example"></a>示例  
 在以下代码中，缓冲区溢出出现在我们将数组复制到本地数组时。 使用 /GS 编译此代码时，不会在堆栈中插入任何 Cookie，因为数组数据类型为指针。 添加 strict_gs_check 杂注会将堆栈 Cookie 强制插入函数堆栈。  
  
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
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/GS （缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)