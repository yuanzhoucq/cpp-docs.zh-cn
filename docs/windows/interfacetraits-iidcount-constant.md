---
title: 'Interfacetraits:: Iidcount 常量 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: c4eab6e0-51f7-4b24-9137-cbcf58e0a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26ccca0c3a9ab3d54c1ffda5e25ed5602cc19ae2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402377"
---
# <a name="interfacetraitsiidcount-constant"></a>InterfaceTraits::IidCount 常量

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
static const unsigned long IidCount = 1;
```

## <a name="remarks"></a>备注

保存数量的接口 Id 与当前相关联**InterfaceTraits**对象。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InterfaceTraits 结构](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)