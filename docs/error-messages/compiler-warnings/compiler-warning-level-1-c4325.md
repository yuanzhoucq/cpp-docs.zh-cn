---
title: 编译器警告 （等级 1） C4325 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4325"></a>编译器警告（等级 1）C4325
**忽略标准节**   
 ***部分*忽略**  
  
 你不能更改的标准部分的属性。 例如：  
  
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