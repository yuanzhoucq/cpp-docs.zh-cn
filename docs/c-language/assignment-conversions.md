---
title: "赋值转换 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e51b6af4006ad3d8b35f9167e4db4e3ea84a89f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="assignment-conversions"></a>赋值转换
在赋值操作中，赋值的类型将转换为接受赋值的变量的类型。 即使转换过程中会丢失信息，C 仍然允许在整型和浮点类型之间进行赋值转换。 使用的转换方法取决于赋值涉及的类型，如[常用算术转换](../c-language/usual-arithmetic-conversions.md)和下列各节中所述：  
  
-   [从带符号整型的转换](../c-language/conversions-from-signed-integral-types.md)  
  
-   [从无符号整型的转换](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [从浮点类型的转换](../c-language/conversions-from-floating-point-types.md)  
  
-   [指针类型之间的转换](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [从其他类型的转换](../c-language/conversions-from-other-types.md)  
  
 虽然 const 左值不能在赋值的左侧使用，但类型限定符不会影响允许的转换。  
  
## <a name="see-also"></a>另请参阅  
 [类型转换](../c-language/type-conversions-c.md)