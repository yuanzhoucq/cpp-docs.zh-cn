---
title: MixIn 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ccea9a053f47ae206cbe5c8412c387f07bd5b52
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603422"
---
# <a name="mixin-structure"></a>MixIn 结构

确保运行时类先后派生自 Windows 运行时接口（如果有）和经典 COM 接口。

## <a name="syntax"></a>语法

```cpp
template<
   typename Derived,
   typename MixInType,
   bool hasImplements = __is_base_of(Details::ImplementsBase,
   MixInType)  
>
struct MixIn;
```

### <a name="parameters"></a>参数

*派生*  
一个类型派生自[实现](../windows/implements-structure.md)结构。

*MixInType*  
基类型。

*hasImplements*  
**true**如果*MixInType*是派生自当前实现基类型;**false**否则为。

## <a name="remarks"></a>备注

如果从 Windows 运行时和 COM 接口派生的类，类声明列表必须先列出任何 Windows 运行时接口，然后任何经典 COM 接口。 **MixIn**可确保按正确的顺序指定接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MixIn`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)