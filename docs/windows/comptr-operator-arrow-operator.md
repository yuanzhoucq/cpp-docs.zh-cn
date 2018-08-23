---
title: 'Comptr:: Operator-&gt;运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417fd11017f9f70ee8cc247898e23741488ae5e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599983"
---
# <a name="comptroperator-gt-operator"></a>Comptr:: Operator-&gt;运算符

检索指向当前模板参数所指定类型的指针。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

## <a name="return-value"></a>返回值

指向当前模板类型名称由指定的类型。

## <a name="remarks"></a>备注

此帮助器函数删除由使用 STDMETHOD 宏导致不必要的开销。 此功能，可以`IUnknown`类型**专用**而不是**虚拟**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)