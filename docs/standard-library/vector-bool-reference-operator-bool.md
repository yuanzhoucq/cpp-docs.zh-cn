---
title: vector&lt;bool&gt;::reference::operator bool | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00ccd9e9ffbab78534c5b6417b7567ba03d007ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963675"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

提供了隐式转换`vector<bool>::reference`到**bool**。

## <a name="syntax"></a>语法

```cpp
operator bool() const;
```

## <a name="return-value"></a>返回值

[vector\<bool>](../standard-library/vector-bool-class.md) 对象元素的布尔值。

## <a name="remarks"></a>备注

`vector<bool>` 对象无法通过此运算符修改。

## <a name="requirements"></a>要求

**标头：**\<vector>

**命名空间：** std

## <a name="see-also"></a>请参阅

[向量\<bool >:: reference 类](../standard-library/vector-bool-reference-class.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
