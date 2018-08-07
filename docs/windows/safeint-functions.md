---
title: SafeInt 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8a0475b5d3ba9053cd5d2df5ffd99ce9292ba8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603450"
---
# <a name="safeint-functions"></a>SafeInt 函数
SafeInt 库提供若干函数，可以使用而无需创建的实例[SafeInt 类](../windows/safeint-class.md)。 如果你想要从整数溢出保护单个数学运算，可以使用这些函数。 如果你想要保护多个数学运算，则应创建**SafeInt**对象。 若要创建效率更高**SafeInt**比使用这些函数多次的对象。  
  
 这些功能，进行比较或执行两个不同类型的参数上的数学运算而无需首先将它们转换为同一类型。  
  
 每个函数有两种模板类型：`T`和`U`。 每个类型可以是一个布尔值、 字符或整数类型。 可以有符号或无符号整型类型和从 8 位到 64 位的任何大小。  
  
## <a name="in-this-section"></a>本节内容  
  
|函数|描述|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|添加两个数字，可防止溢出。|  
|[SafeCast](../windows/safecast.md)|将转换为一种类型的另一种类型的参数。|  
|[SafeDivide](../windows/safedivide.md)|使两个数字相除，防止被零除。|  
|[SafeEquals](../windows/safeequals.md)， [SafeGreaterThan](../windows/safegreaterthan.md)， [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)， [SafeLessThan](../windows/safelessthan.md)， [SafeLessThanEquals](../windows/safelessthanequals.md)， [SafeNotEquals](../windows/safenotequals.md)|比较两个数字。 这些函数，可以比较两个不同类型的数字，而不更改其类型。|  
|[SafeModulus](../windows/safemodulus.md)|执行取模运算对两个数字。|  
|[SafeMultiply](../windows/safemultiply.md)|两个数字相乘，这样可以避免溢出。|  
|[SafeSubtract](../windows/safesubtract.md)|两个数字相减，可防止溢出。|  
  
## <a name="related-sections"></a>相关章节  
  
|节|描述|  
|-------------|-----------------|  
|[SafeInt 类](../windows/safeint-class.md)|**SafeInt**类。|  
|[SafeIntException 类](../windows/safeintexception-class.md)|特定于 SafeInt 库的异常类。|