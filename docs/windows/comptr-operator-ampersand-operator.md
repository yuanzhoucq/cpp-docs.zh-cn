---
title: 'Comptr:: Operator&amp;运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f513ac83e0ee83109f42cf87b80b4fcc4960db1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598598"
---
# <a name="comptroperatoramp-operator"></a>Comptr:: Operator&amp;运算符

释放与此关联的接口**ComPtr**对象，然后检索的地址**ComPtr**对象。

## <a name="syntax"></a>语法

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

## <a name="return-value"></a>返回值

对当前的弱引用**ComPtr**。

## <a name="remarks"></a>备注

此方法不同于[comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) ，此方法释放接口指针的引用。 使用`ComPtr::GetAddressOf`时需要的接口指针的地址但不是想要发布该接口。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)