---
title: 'Implements:: casttounknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586353"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown 方法

获取一个指针指向基础`IUnknown`接口。

## <a name="syntax"></a>语法

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>返回值

此操作始终成功并返回`IUnknown`指针。

## <a name="remarks"></a>备注

内部帮助器函数。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Implements 结构](../windows/implements-structure.md)