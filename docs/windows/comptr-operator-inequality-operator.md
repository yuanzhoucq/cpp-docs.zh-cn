---
title: 'Comptr:: Operator ！ = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce6e3357582abe94fdc538932e49e773c37f116b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384685"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= 运算符

指示两个**ComPtr**对象是否不相等。

## <a name="syntax"></a>语法

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
对引用**ComPtr**对象。

*b*<br/>
对另一个引用**ComPtr**对象。

## <a name="return-value"></a>返回值

第一个运算符产生 **，则返回 true**如果对象不等于对象*b*; 否则为**false**。

第二个和第三个运算符会产生 **，则返回 true**如果对象是否不等于**nullptr**; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)<br/>
[ComPtr 类](../windows/comptr-class.md)