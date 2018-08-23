---
title: 'Handlet:: Detach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b66d5c65dd084da564067cd62242b315f6da182
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591369"
---
# <a name="handletdetach-method"></a>HandleT::Detach 方法

取消关联当前**HandleT**对象从其基础句柄。

## <a name="syntax"></a>语法

```cpp
typename HandleTraits::Type Detach();
```

## <a name="return-value"></a>返回值

基础句柄。

## <a name="remarks"></a>备注

此操作完成后，当前**HandleT**设置为无效状态。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HandleT 类](../windows/handlet-class.md)