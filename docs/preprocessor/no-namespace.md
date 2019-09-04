---
title: no_namespace 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220738"
---
# <a name="no_namespace-import-attribute"></a>no_namespace 导入属性

**C++相关**

指定编译器不生成命名空间名称。

## <a name="syntax"></a>语法

> **#import***类型库***no_namespace**

## <a name="remarks"></a>备注

`#import` 标头文件中的类型库内容通常在命名空间中定义。 命名空间名称是在原始 IDL `library`文件的语句中指定的。 如果指定了**no_namespace**特性, 则编译器不会生成此命名空间。

如果要使用不同的命名空间名称, 请改为使用[rename_namespace](../preprocessor/rename-namespace.md)特性。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
