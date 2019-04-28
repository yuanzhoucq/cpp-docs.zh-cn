---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: f6bd60de02bf0166d5cf0b0cd1bc1de56ceda5bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326555"
---
# <a name="nonamespace"></a>no_namespace
**C++特定**

指定命名空间的名称不由编译器生成。

## <a name="syntax"></a>语法

```
no_namespace
```

## <a name="remarks"></a>备注

`#import` 标头文件中的类型库内容通常在命名空间中定义。 中指定的命名空间名称`library`语句的原始 IDL 文件。 如果**no_namespace**指定属性，则编译器不生成此命名空间。

如果你想要使用不同的命名空间名称，然后使用[rename_namespace](../preprocessor/rename-namespace.md)特性。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)