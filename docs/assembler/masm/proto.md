---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 24ec2a9abc6c8b76fc81f6d412019296c53160f4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74394758"
---
# <a name="proto"></a>PROTO

原型函数或过程。 可以使用[INVOKE](invoke.md)指令通过 PROTO 指令调用函数原型。

## <a name="syntax"></a>语法

> *标签* **PROTO** ⟦*距离*⟧⟦*language-类型*⟧⟦ __，__ ⟦*参数*⟧ __：__ *tag* .。。⟧

### <a name="parameters"></a>参数

*标签*\
原型函数的名称。

*距离*\
可有可无在16位内存模型中用于重写默认值，并指示近**距离或远**调用。

*语言类型*\
可有可无设置过程和公共符号的调用和命名约定。 支持的约定包括：

- 32位**平面**模型： **C**， **STDCALL**

- 16位模型： **C**， **BASIC**， **FORTRAN**， **PASCAL**， **SYSCALL**， **STDCALL**

*参数*\
函数参数的可选名称。

*标记*\
函数参数的类型。

*参数*和*标记*参数可以多次出现，每个传递的参数一次。

## <a name="example"></a>示例

此示例显示了一个名为 `addup3` 的函数的**PROTO**声明，该函数使用**临近**调用来重写过程调用的16位模型默认值，并对堆栈参数和返回值使用**C**调用约定。 它采用两个参数：一个**词**和一个**VARARG**。

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[.模型引用](dot-model.md)
