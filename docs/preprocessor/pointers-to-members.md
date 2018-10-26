---
title: pointers_to_members |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs:
- C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c37828e88156b5be10abdf2fc41c396fdef33784
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071831"
---
# <a name="pointerstomembers"></a>pointers_to_members

**C + + 专用**

指定是否可以在类成员关联的类定义之前声明指向类成员的指针，以及类成员是否用于控制指针大小和解释指针所需的代码。

## <a name="syntax"></a>语法

```
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )
```

## <a name="remarks"></a>备注

可以将放置**pointers_to_members**杂注中使用的替代方法作为源文件[/vmx](../build/reference/vmb-vmg-representation-method.md)编译器选项或[继承关键字](../cpp/inheritance-keywords.md)。

*指针声明*参数指定是否已声明指针到成员关联的函数定义之前或之后。 *指针声明*参数是以下两个符号之一：

|参数|注释|
|--------------|--------------|
|*full_generality*|生成安全的（有时并非最佳）代码。 您使用*full_generality*如果关联的类定义之前声明指向成员的任何指针。 此自变量始终使用由指定的指针表示形式*大多数常规表示*参数。 等效于 /vmg。|
|*best_case*|使用指向成员的所有指针的最佳大小写表示形式生成安全的最佳代码。 要求在声明指向类成员的指针之前定义此类。 默认值是*best_case*。|

*大多数常规表示*参数指定编译器可以安全地使用引用指向翻译单元中的类的成员的任何指针的最小指针表示形式。 自变量可以是下列项之一：

|参数|注释|
|--------------|--------------|
|*single_inheritance*|最常规的表示形式为单一继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为多重继承或虚拟继承，则会导致出现错误。|
|*multiple_inheritance*|最常规的表示形式为多重继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为虚拟继承，则会导致出现错误。|
|*virtual_inheritance*|最常规的表示形式为虚拟继承（指向成员函数的指针）。 绝不会导致出现错误。 这是默认参数时`#pragma pointers_to_members(full_generality)`使用。|

> [!CAUTION]
> 我们建议您先放**pointers_to_members**杂注仅在你想要产生效果，源代码文件并且仅在任何`#include`指令。 此做法可以减小杂注影响其他文件以及为同一变量、函数或类名意外指定多个定义的风险。

## <a name="example"></a>示例

```
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

## <a name="end-c-specific"></a>结束 C++ 专用

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)