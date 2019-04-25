---
title: 表达式中的数组
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184370"
---
# <a name="arrays-in-expressions"></a>表达式中的数组

当数组类型的标识符出现在表达式中以外`sizeof`，地址的 (**&**)，或初始化的引用，它将转换为指向第一个数组元素的指针。 例如：

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指针 `psz` 指向数组 `szError1` 的第一个元素。 请注意，与指针不同，数组不是可修改的左值。 因此，以下赋值是非法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>请参阅

[数组](../cpp/arrays-cpp.md)