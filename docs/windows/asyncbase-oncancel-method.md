---
title: 'Asyncbase:: Oncancel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs:
- C++
helpviewer_keywords:
- OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6297b2d9313a8bc2c7a4f90632affa054c49c662
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595262"
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel 方法

当在派生类中重写时取消异步操作。

## <a name="syntax"></a>语法

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)  
[AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)