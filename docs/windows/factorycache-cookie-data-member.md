---
title: 'Factorycache:: Cookie 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs:
- C++
helpviewer_keywords:
- cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97af2db56cab99412faf35efa8cd351946ab4828
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410294"
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie 数据成员

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

## <a name="remarks"></a>备注

包含一个值，用于标识已注册的 Windows 运行时或 COM 类对象，并随后用于取消注册该对象。

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[FactoryCache 结构](../windows/factorycache-structure.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)