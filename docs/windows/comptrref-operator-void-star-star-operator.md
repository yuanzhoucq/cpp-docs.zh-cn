---
title: 'Comptrref:: Operator void * * 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b38dac2082e47e94e4bd52af50d77327f5ef4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590684"
---
# <a name="comptrrefoperator-void-operator"></a>Comptrref:: Operator void\* \*运算符

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
operator void**() const;
```

## <a name="remarks"></a>备注

删除当前**ComPtrRef**对象，将强制转换到由表示的接口指针**ComPtrRef**对象作为指针-到-指针-若要**void**，，然后返回转换的指针。

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[ComPtrRef 类](../windows/comptrref-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)