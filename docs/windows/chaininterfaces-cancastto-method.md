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
ms.openlocfilehash: 8398f0bd4d9fdc786926782b13ebcac913a6a351
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612865"
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

*riid*  
接口 ID。

*ppv*  
指向已成功转换的最后一个接口 ID 的指针。

## <a name="return-value"></a>返回值

**true**如果所有的强制转换操作成功; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ChainInterfaces 结构](../windows/chaininterfaces-structure.md)