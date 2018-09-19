---
title: _com_ptr_t::QueryInterface |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0add1d8f3fc73f78cee3e10642d7b5a12968a6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106862"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft 专用**

调用**QueryInterface**成员函数的`IUnknown`上封装的接口指针。

## <a name="syntax"></a>语法

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>参数

*iid*<br/>
`IID` 接口指针。

*p*<br/>
原始接口指针。

## <a name="remarks"></a>备注

调用`IUnknown::QueryInterface`上使用指定的封装的接口指针`IID`，并返回在生成的原始接口指针*p*。 此例程将返回 HRESULT，指示成功或失败。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)