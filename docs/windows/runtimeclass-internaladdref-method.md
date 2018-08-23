---
title: 'Runtimeclass:: Internaladdref 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
dev_langs:
- C++
helpviewer_keywords:
- InternalAddRef method
ms.assetid: b8ed7f93-83d8-47ec-988c-98fe65104e7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e0d2b6d41598195b2615e4d6b4a8585d1ca1cf2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599720"
---
# <a name="runtimeclassinternaladdref-method"></a>RuntimeClass::InternalAddRef 方法

递增引用计数与当前**RuntimeClass**对象。

## <a name="syntax"></a>语法

```cpp
ULONG InternalAddRef();
```

## <a name="return-value"></a>返回值

在生成的引用计数。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)