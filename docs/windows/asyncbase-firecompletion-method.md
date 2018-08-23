---
title: 'Asyncbase:: Firecompletion 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19b796b1fbc618bb909b186aa86d3c893c8536c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600251"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion 方法

调用完成事件处理程序，或重置内部进行委托。

## <a name="syntax"></a>语法

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

## <a name="remarks"></a>备注

第一个版本**FireCompletion()** 重置内部进度委托变量。 如果异步操作已完成，第二个版本调用完成事件处理程序。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)