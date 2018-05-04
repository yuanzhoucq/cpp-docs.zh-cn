---
title: _variant_t 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebe850e4b0d0d9fd352df0e60c4ea0737b9fd8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="variantt-class"></a>_variant_t 类
**Microsoft 专用**  
  
 A`_variant_t`对象所封装`VARIANT`数据类型。 类管理资源分配和释放和函数调用**VariantInit**和**VariantClear**根据。  
  
### <a name="construction"></a>构造  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|构造 `_variant_t` 对象。|  
  
### <a name="operations"></a>操作  
  
|||  
|-|-|  
|[附加](../cpp/variant-t-attach.md)|将附加**VARIANT**对象插入`_variant_t`对象。|  
|[清除](../cpp/variant-t-clear.md)|清除封装**VARIANT**对象。|  
|[ChangeType](../cpp/variant-t-changetype.md)|类型更改`_variant_t`到指示的对象**VARTYPE**。|  
|[分离](../cpp/variant-t-detach.md)|分离封装**VARIANT**从此对象`_variant_t`对象。|  
|[SetString](../cpp/variant-t-setstring.md)|将字符串分配给此 `_variant_t` 对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](../cpp/variant-t-operator-equal.md)|将新值赋给现有 `_variant_t` 对象。|  
|[运算符 = =、 ！ =](../cpp/variant-t-relational-operators.md)|比较两个 `_variant_t` 对象是否相等。|  
|[提取器](../cpp/variant-t-extractors.md)|从封装中提取数据**VARIANT**对象。|  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>要求  
 **标头：** \<comutil.h >  
  
 **Lib:** 对 comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)