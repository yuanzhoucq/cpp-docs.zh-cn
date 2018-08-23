---
title: 同步 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.synchronize
dev_langs:
- C++
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a72d305cfae3ba76a7c61ee7f2a6a604e6832631
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604691"
---
# <a name="synchronize"></a>synchronize

同步到目标方法的访问。

## <a name="syntax"></a>语法

```cpp
[synchronize]
```

## <a name="remarks"></a>备注

**同步**c + + 属性实现为同步对象的目标方法的支持。 同步通过控制目标方法的访问权限允许多个对象使用公共资源 （如类的方法）。

此属性由插入该代码调用了正确`Lock`目标方法的开头 （由线程模型） 的方法。 该方法退出时,`Unlock`自动调用。 有关这些函数的详细信息，请参阅[CComAutoThreadModule::Lock](../atl/reference/ccomautothreadmodule-class.md#lock)

此属性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果`progid`应用时，`vi_progid`和`coclass`也会应用。

## <a name="example"></a>示例

下面的代码提供的同步`UpdateBalance`方法的`CMyClass`对象。

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
 threading(both),
 vi_progid("MyProject.MyClass"),
 progid("MyProject.MyClass.1"),
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|类方法方法|
|**可重复**|否|
|**必需的特性**|一个或多个以下： `coclass`， `progid`，或`vi_progid`。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[COM 特性](../windows/com-attributes.md)  