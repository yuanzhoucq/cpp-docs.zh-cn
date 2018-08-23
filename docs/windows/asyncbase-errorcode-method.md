---
title: 'Asyncbase:: Errorcode 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7336824d04745440a1f6152ebacfed2afc62258e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602373"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 方法

检索当前的异步操作的错误代码。

## <a name="syntax"></a>语法

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>参数

*error*  
此操作存储当前的错误代码的位置。

## <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)