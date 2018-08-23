---
title: 'Comptrref:: Operator = = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abf78644f7cad90d25d365f6237407aeaeb6917b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575698"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== 运算符

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>参数

*a*  
对引用**ComPtrRef**对象。

*b*  
对另一个引用**ComPtrRef**对象或到匿名类型的指针 (`void*`)。

## <a name="return-value"></a>返回值

第一个运算符产生 **，则返回 true**如果对象是否等于对象*b*; 否则为**false**。

第二个和第三个运算符会产生 **，则返回 true**如果对象等于**nullptr**; 否则为**false**。

第四个和第五个运算符会产生 **，则返回 true**如果对象是否等于对象*b*; 否则为**false**。

## <a name="remarks"></a>备注

指示两个**ComPtrRef**对象是否相等。

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)  
[ComPtrRef 类](../windows/comptrref-class.md)