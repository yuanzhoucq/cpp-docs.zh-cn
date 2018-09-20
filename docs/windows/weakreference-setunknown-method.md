---
title: 'Weakreference:: Setunknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6fc7accbad5633bd57d7fceb16f82edb82d80f4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422488"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>参数

*unk*<br/>
一个指向`IUnknown`接口的对象。

## <a name="remarks"></a>备注

设置当前的强引用**WeakReference**对象与指定的接口指针。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[WeakReference 类](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)