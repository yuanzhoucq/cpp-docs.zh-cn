---
title: Varargs |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380503"
---
# <a name="varargs"></a>Varargs
如果通过 varargs （例如，省略号自变量） 传递的参数，实质上是正常的参数传递应用包括将溢出的第五个和后续参数。 它被调用采用其地址的转储自变量被调用方的责任。 仅对于浮点值，整数和浮点寄存器将包含的 float 值在被调用方期望整数寄存器中的值的情况下。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)