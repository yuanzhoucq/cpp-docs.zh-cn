---
title: 'Implements:: fillarraywithiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c65e2d47d466b223acf19589e5966a05762605e3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611559"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid 方法

将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。

## <a name="syntax"></a>语法

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*  
一个从零开始的索引，该值指示此操作的起始数组元素。 此操作完成后，*索引*都会增加 1。

*iid*  
类型 IID 的数组。

## <a name="remarks"></a>备注

内部帮助器函数。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Implements 结构](../windows/implements-structure.md)