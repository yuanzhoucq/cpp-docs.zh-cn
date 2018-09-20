---
title: 'Chaininterfaces:: Cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 752c3598a38117506154b0a2b7d7d3e578bf3c3e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417639"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo 方法

指示指定的接口 ID 是否可以转换为每个定义的非默认模板参数的专用化。

## <a name="syntax"></a>语法

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppv*<br/>
指向已成功转换的最后一个接口 ID 的指针。

## <a name="return-value"></a>返回值

**true**如果所有的强制转换操作成功; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ChainInterfaces 结构](../windows/chaininterfaces-structure.md)