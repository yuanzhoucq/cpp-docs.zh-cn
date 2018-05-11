---
title: 特性上下文 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e220eb0e7eb80d01d70aed82e773c46fe6704c7d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="attribute-contexts"></a>特性上下文
可以使用四个基本字段描述 c + + 特性： 它们可以应用到的目标 (**适用于**)，如果它们是可重复的还是不 (**可重复**)，则需要其他特性 (是否存在**必需的属性**)，并与其他属性不兼容 (**无效的特性**)。 这些字段在每个属性的参考主题的相关表中列出。 下面描述了每个这些字段。  
  
## <a name="applies-to"></a>适用于  
 此字段描述是指定的属性的合法目标的不同 c + + 语言元素。 例如，如果属性中指定"类"**适用于**字段，这指示该属性可以只能应用于合法的 c + + 类。 如果该属性应用于类的成员函数，则会导致语法错误。  
  
 有关详细信息，请参阅[按用法分的特性](../windows/attributes-by-usage.md)。  
  
## <a name="repeatable"></a>可重复  
 此字段，指出是否该属性可以重复应用于相同的目标。 大部分属性不是可重复的。  
  
## <a name="required-attributes"></a>必需的特性  
 此字段列出了需要其他特性存在指定的属性才能正常工作 （即，应用到相同目标）。 它是常见的属性以包含此字段的任何条目。  
  
## <a name="invalid-attributes"></a>无效的特性  
 此字段会列出与指定的属性不兼容的其他特性。 它是常见的属性以包含此字段的任何条目。  
  
## <a name="see-also"></a>请参阅  
 [C++ 特性参考](../windows/cpp-attributes-reference.md)