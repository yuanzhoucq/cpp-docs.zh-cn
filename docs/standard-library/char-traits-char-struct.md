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
ms.openlocfilehash: 1150de3c94f8a656d46d54b673cb2d08dc05a7be
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959321"
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt; 结构

专用化的模板结构的结构**char_traits\<CharType >** 类型的元素**char**。

## <a name="syntax"></a>语法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>备注

专用化允许结构利用库函数处理此类型的对象**char**。

## <a name="example"></a>示例

查看模板类 [char_traits 类](../standard-library/char-traits-struct.md) 的 typedef 和成员函数
