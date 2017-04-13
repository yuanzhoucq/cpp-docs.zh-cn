---
title: "编译器错误 C3415 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3415
dev_langs:
- C++
helpviewer_keywords:
- C3415
ms.assetid: fa2db8ab-2820-4ec3-a740-fb5e2adcfb29
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: aeb26c5a3b1add0f3b8ec3eb9ba9ae2c20fb094e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3415"></a>编译器错误 C3415
找到多个“section_name”节，它们具有不同的属性（“value”）  
  
 中指定了冲突值[部分](../../preprocessor/section.md)杂注。  
  
 `value`是部分中，如 ntimage.h 中的当前设置。 例如:   
  
```  
// Section contains extended relocations.  
#define IMAGE_SCN_LNK_NRELOC_OVFL            0x01000000    
// Section can be discarded.  
#define IMAGE_SCN_MEM_DISCARDABLE            0x02000000    
// Section is not cachable.  
#define IMAGE_SCN_MEM_NOT_CACHED             0x04000000    
// Section is not pageable.  
#define IMAGE_SCN_MEM_NOT_PAGED              0x08000000    
// Section is shareable.  
#define IMAGE_SCN_MEM_SHARED                 0x10000000    
// Section is executable.  
#define IMAGE_SCN_MEM_EXECUTE                0x20000000    
// Section is readable.  
#define IMAGE_SCN_MEM_READ                   0x40000000    
// Section is writeable.  
#define IMAGE_SCN_MEM_WRITE                  0x80000000    
```  
  
 下面的示例生成 C3415：  
  
```  
// C3415.cpp  
#pragma section("mysec1",write)  
#pragma section("mysec1",read)   // C3415  
```
