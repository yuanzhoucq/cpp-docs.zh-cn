---
title: 'Comptrrefbase:: Operator IInspectable * * 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f711a9d1f5fe92e5f35bf333fc0b3473fc0eebf4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604401"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>Comptrrefbase:: Operator IInspectable\* \*运算符

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>备注

将当前[ptr_](../windows/comptrrefbase-ptr-data-member.md)数据成员添加到指针-到-a-指针-到`IInspectable`接口。

如果发出错误当前**ComPtrRefBase**也不是派生`IInspectable`。

此强制转换为可用才`__WRL_CLASSIC_COM__`定义。

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[ComPtrRefBase 类](../windows/comptrrefbase-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)