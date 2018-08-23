---
title: 'Asyncbase:: Continueasyncoperation 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83d7a0bb5eadede42d2572d5ebc5a02a0fe9a0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607180"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation 方法

确定异步操作是否会继续进行处理，或者应该中止。

## <a name="syntax"></a>语法

```cpp
inline bool ContinueAsyncOperation();
```

## <a name="return-value"></a>返回值

**true**异步操作的当前状态是否*启动*，这意味着该操作应继续。 否则为**false**，这意味着该操作应该中止。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)