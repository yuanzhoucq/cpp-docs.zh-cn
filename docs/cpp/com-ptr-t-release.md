---
title: _com_ptr_t::Release |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444f56c1a999f09a79d725173c9f0f19399ab363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118357"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft 专用**

调用**发行**成员函数的`IUnknown`上封装的接口指针。

## <a name="syntax"></a>语法

```
void Release( );
```

## <a name="remarks"></a>备注

调用`IUnknown::Release`封装的接口指针上引发`E_POINTER`错误如果此接口指针为 NULL。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)