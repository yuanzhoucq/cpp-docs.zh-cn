---
title: 特性上下文 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f34fb2a019e922f7eed3a430e62be272f9d57dce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427285"
---
# <a name="attribute-contexts"></a>特性上下文
可以使用四个基本字段描述 c + + 特性： 它们可以应用到的目标 (**适用于**)，如果它们是可重复的还是不 (**Repeatable**)，则所需的其他属性 (存在**所需属性**)，并与其他属性的不兼容性 (**无效属性**)。 在每个属性的参考主题中的相关表中列出这些字段。 下面描述了每个字段。
  
## <a name="applies-to"></a>适用于

此字段描述了不同的 c + + 语言元素的指定属性的合法目标。 例如，如果属性中指定"的类"**适用于**字段中，这表示该属性可以仅应用于合法的 c + + 类。 如果该特性应用于类的成员函数，会产生语法错误。
  
有关详细信息，请参阅[按使用情况的特性](../windows/attributes-by-usage.md)。
  
## <a name="repeatable"></a>可重复

此字段规定是否该属性可以重复应用于同一个目标。 属性的大多数都不是可重复。
  
## <a name="required-attributes"></a>必需的特性

此字段中列出了需要其他属性指定的属性才能正常运行 （即，应用到同一目标） 存在。 它是常见的一个属性以包含此字段的任何条目。
  
## <a name="invalid-attributes"></a>无效的属性

此字段中列出了与指定的特性不兼容的其他属性。 它是常见的一个属性以包含此字段的任何条目。
  
## <a name="see-also"></a>请参阅

[C++ 特性参考](../windows/cpp-attributes-reference.md)