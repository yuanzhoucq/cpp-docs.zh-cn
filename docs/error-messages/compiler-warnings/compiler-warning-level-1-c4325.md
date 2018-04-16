---
title: "编译器警告 （等级 1） C4325 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab31150efc02601d7392470198e162e979ac4917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4325"></a>编译器警告（等级 1）C4325
**忽略标准节**   
 ***部分*忽略**  
  
 你不能更改的标准部分的属性。 例如:  
  
```  
#pragma section(".sdata", long)  
```  
  
 这将覆盖`.sdata`标准部分使用**短**数据类型，为**长**数据类型。  
  
 标准节你不能更改其属性包括：  
  
-   .data  
  
-   .sdata  
  
-   .bss  
  
-   .sbss  
  
-   .text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 可能在以后添加其他部分。  
  
## <a name="see-also"></a>请参阅  
 [section](../../preprocessor/section.md)