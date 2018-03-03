---
title: "SafeInt 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ae482b7f58d64a46b82b32c6c6d62d7f69f0dce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="safeint-functions"></a>SafeInt 函数
SafeInt 库提供你可以使用而无需创建的实例的多个函数[SafeInt 类](../windows/safeint-class.md)。 如果你想要从整数溢出保护单个数学运算，你可以使用这些函数。 如果你想要保护多个数学运算，则应创建`SafeInt`对象。 它会更加高效创建`SafeInt`对象而不是若要使用这些函数多次。  
  
 这些函数使您能够比较或对执行数学运算两种不同类型的参数而无需先将它们转换为同一类型。  
  
 其中每个函数具有两种模板类型：`T`和`U`。 上述每种类型可以是布尔值、 字符或整数类型。 可以有符号或无符号整型类型和任何大小从 8 位到 64 位。  
  
## <a name="in-this-section"></a>本节内容  
  
|函数|描述|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|添加两个数字并防止溢出。|  
|[SafeCast](../windows/safecast.md)|将一种类型的另一个类型参数强制转换。|  
|[SafeDivide](../windows/safedivide.md)|使两个数字相除，防止被零除。|  
|[SafeEquals](../windows/safeequals.md)， [SafeGreaterThan](../windows/safegreaterthan.md)， [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)， [SafeLessThan](../windows/safelessthan.md)， [SafeLessThanEquals](../windows/safelessthanequals.md)，[SafeNotEquals](../windows/safenotequals.md)|比较两个数字。 这些函数使你能够比较而无需更改其类型的两个不同类型的数字。|  
|[SafeModulus](../windows/safemodulus.md)|执行取模操作对两个数字。|  
|[SafeMultiply](../windows/safemultiply.md)|两个数字相乘，这样可以避免溢出。|  
|[SafeSubtract](../windows/safesubtract.md)|两个数字相减，这样可以避免溢出。|  
  
## <a name="related-sections"></a>相关章节  
  
|节|描述|  
|-------------|-----------------|  
|[SafeInt 类](../windows/safeint-class.md)|`SafeInt` 类。|  
|[SafeIntException 类](../windows/safeintexception-class.md)|特定于 SafeInt 库的异常类。|