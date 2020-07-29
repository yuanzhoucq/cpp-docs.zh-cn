---
title: char_traits&lt;char&gt; 结构
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: 04e3a3d067c7fd0e4513d1e1e4463ff6e9f7fe22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224885"
---
# <a name="char_traitsltchargt-struct"></a>char_traits&lt;char&gt; 结构

作为模板结构的专用化的结构，该**结构 \<CharType> char_traits**类型为的元素 **`char`** 。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>备注

专用化允许结构利用操作此类型对象的库函数 **`char`** 。

## <a name="example"></a>示例

请参阅类模板[Char_traits 类](../standard-library/char-traits-struct.md)的 typedef 和成员函数
