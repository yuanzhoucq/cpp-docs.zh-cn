---
title: "堆常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs: C++
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5b529519840df87d829c34cd8bddf123b96754e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="heap-constants"></a>堆常量
## <a name="syntax"></a>语法  
  
```  
  
#include <malloc.h>  
  
```  
  
## <a name="remarks"></a>备注  
 这些常量提供表示堆状态的返回值。  
  
|常量|含义|  
|--------------|-------------|  
|`_HEAPBADBEGIN`|初始头信息未找到或无效。|  
|`_HEAPBADNODE`|找到错误节点，或堆已损坏。|  
|`_HEAPBADPTR`|_HEAPINFO 结构的 _pentry 字段不包含堆中的有效指针（仅限 `_heapwalk` 例程）。|  
|`_HEAPEMPTY`|尚未初始化堆。|  
|`_HEAPEND`|已成功到达堆的结尾处（仅限 `_heapwalk` 例程）。|  
|`_HEAPOK`|堆是一致的（仅限 `_heapset` 和 `_heapchk` 例程）。 目前未出现错误；_HEAPINFO 结构包含下一个条目的信息（仅限 `_heapwalk` 例程）。|  
  
## <a name="see-also"></a>另请参阅  
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapset](../c-runtime-library/heapset.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全局常量](../c-runtime-library/global-constants.md)