---
title: 'Asyncbase:: Trytransitiontoerror 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1244b87410a09996d946408ff77dbb552b339c85
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591149"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError 方法

指示指定的错误代码是否可以修改的内部错误状态。

## <a name="syntax"></a>语法

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>参数

*error*  
错误的 HRESULT。

## <a name="return-value"></a>返回值

**true**内部错误状态已更改; 否则为如果**false**。

## <a name="remarks"></a>备注

仅当错误状态已设置为，则为 S_OK，则此操作修改的错误状态。 如果错误状态已经是错误，已取消、 已完成，或已关闭，则此操作无效。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)