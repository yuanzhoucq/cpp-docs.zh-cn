---
title: char_traits&lt;char&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: ccb08f3e505122757080129b36558490456fc2c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688322"
---
# <a name="char_traitsltchargt-struct"></a>char_traits&lt;char&gt; 结构

一个结构，它是模板结构**char_traits \<CharType >** 到类型**char**的元素的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>备注

专用化允许结构利用操作此类型**char**的对象的库函数。

## <a name="example"></a>示例

请参阅类模板[Char_traits 类](../standard-library/char-traits-struct.md)的 typedef 和成员函数
