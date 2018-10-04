---
title: 同步 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 740d99bfbc0da4c290a09a95f5d4f8f227a11fc8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790387"
---
# <a name="synchronize"></a>synchronize

同步到目标方法的访问。

## <a name="syntax"></a>语法

```cpp
[synchronize]
```

## <a name="remarks"></a>备注

**同步**c + + 属性实现为同步对象的目标方法的支持。 同步通过控制目标方法的访问权限允许多个对象使用公共资源 （如类的方法）。

此属性由插入该代码调用了正确`Lock`目标方法的开头 （由线程模型） 的方法。 该方法退出时,`Unlock`自动调用。 有关这些函数的详细信息，请参阅[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

此属性要求[组件类](coclass.md)， [progid](progid.md)，或[vi_progid](vi-progid.md)属性 （或隐含其中一种的另一个属性） 也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果`progid`应用时，`vi_progid`和`coclass`也会应用。

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

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[COM 特性](com-attributes.md)  