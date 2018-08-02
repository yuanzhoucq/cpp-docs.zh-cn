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
ms.openlocfilehash: 19e04f5415f9f7a736371c888dff7559df6c6c66
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462331"
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

此强制转换为可用才 **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** 定义。

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅
[ComPtrRefBase 类](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)