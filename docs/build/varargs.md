---
title: "Varargs |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3d22a5c3f20480d1e904ec8e087114385ba7ee9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="varargs"></a>Varargs
如果通过 varargs （例如，省略号自变量） 传递的参数，实质上是正常的参数传递应用包括将溢出的第五个和后续参数。 它被调用采用其地址的转储自变量被调用方的责任。 仅对于浮点值，整数和浮点寄存器将包含的 float 值在被调用方期望整数寄存器中的值的情况下。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)