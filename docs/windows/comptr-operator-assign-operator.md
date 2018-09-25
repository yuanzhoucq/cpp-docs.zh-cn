---
title: 'Comptr:: Operator = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 177d6ebde6a4611e9a08dc3dade63bd6c3acc3fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401623"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= 运算符

将值分配给当前**ComPtr**。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)  
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>参数

*U*<br/>
一个类。

*other*<br/>
指针、 引用或右值引用类型或另一**ComPtr**。

## <a name="return-value"></a>返回值

对当前的引用**ComPtr**。

## <a name="remarks"></a>备注

此运算符的第一个版本将为空值分配给当前**ComPtr**。

在第二个版本中，如果分配的接口指针不是与当前**ComPtr**接口指针，第二个接口指针分配给当前**ComPtr**。

在第三个版本中，分配的接口指针分配给当前**ComPtr**。

在第四个版本中，如果分配值的接口指针不是与当前**ComPtr**接口指针，第二个接口指针分配给当前**ComPtr**。

第五个版本是复制运算符;对引用**ComPtr**分配给当前**ComPtr**。

第六个版本是使用复制运算符移动语义;右值引用**ComPtr**如果任何类型是静态的强制转换，然后分配给当前**ComPtr**。

第七个版本是使用复制运算符移动语义;右值引用**ComPtr**类型的*U*是静态然后强制转换和分配给当前**ComPtr**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)