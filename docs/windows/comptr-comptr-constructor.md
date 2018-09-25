---
title: 'Comptr:: Comptr 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05440f9d6a7f243432dfa118cf1e137d9c5428d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429313"
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr 构造函数

初始化的新实例**ComPtr**类。 重载提供默认、复制、移动和转换构造函数。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)  
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>参数

*U*<br/>
类型*其他*参数。

*other*<br/>
类型的对象*U*。

## <a name="return-value"></a>返回值

## <a name="remarks"></a>备注

第一个构造函数是默认构造函数，哪些隐式创建一个空的对象。 第二个构造函数指定[__nullptr](../windows/nullptr-cpp-component-extensions.md)，其显式创建一个空的对象。

第三个构造函数创建从指针指定的对象的对象。

第四个和第五个构造函数是复制构造函数。 第五个构造函数将对象转换为当前类型的情况下将其复制。

第六个和第七个构造函数是移动构造函数。 第七个构造函数移动对象，如果转换为当前的类型。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)