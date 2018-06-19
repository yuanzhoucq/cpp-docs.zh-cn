---
title: char_traits&lt;char&gt; 结构 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a20e9c1df241feb8dd7f16891f1e2a67068f772
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840389"
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt; 结构

此结构是模板结构 **char_traits\<CharType>** 对 `char` 类型的一个元素的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理此 `char` 类型的对象。

## <a name="example"></a>示例

查看模板类 [char_traits 类](../standard-library/char-traits-struct.md) 的 typedef 和成员函数
