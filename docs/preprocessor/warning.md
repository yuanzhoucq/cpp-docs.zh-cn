---
title: 警告杂注
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: d8b110d459bba1e0b7e2fd6e2c95e7eed638fc99
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416190"
---
# <a name="warning-pragma"></a>警告杂注

启用编译器警告消息的行为的选择性修改。

## <a name="syntax"></a>语法

> **#pragma 警告（** \
> &nbsp;&nbsp;&nbsp;&nbsp;*警告-说明符* **：** *warning-list*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *warning-说明符* **：** *warning-number-list* ...] **）** \
> **#pragma warning （push** [ **，** *n* ] **）** \
> **#pragma 警告（pop）**

## <a name="remarks"></a>备注

以下警告说明符参数可用。

|警告说明符|含义|
|------------------------|-------------|
|*1，2，3，4*|将给定级别应用于指定的警告。 还会打开默认情况下处于关闭状态的指定警告。|
|default|将警告行为重置为其默认值。 还会打开默认情况下处于关闭状态的指定警告。 警告将在其默认存档级别生成。<br /><br /> 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|*disable*|不要发出指定的警告消息。|
|*error*|将指定警告报告为错误。|
|*once*|只显示指定消息一次。|
|*取消*|将杂注的当前状态推送到堆栈上，禁用下一行的指定警告，然后弹出警告堆栈，从而重置杂注状态。|

以下代码语句演示了 `warning-number-list` 参数可包含多个警告编号，并演示了可在同一杂注指令中指定多个 `warning-specifier` 参数。

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

此指令在功能上等效于以下代码：

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning C4385 only once.
#pragma warning( once : 4385 )

// Report warning C4164 as an error.
#pragma warning( error : 164 )
```

编译器将 4000 添加到 0 和 999 之间的任何警告编号。

对于4700-4999 范围（即与代码生成关联的警告编号），当编译器遇到函数定义时生效的警告的状态将对函数的其余部分有效。 使用函数中的**警告**杂注来更改大于4699的警告编号的状态仅在函数的末尾后生效。 下面的示例演示**警告**杂注的正确位置，以禁用代码生成警告消息，然后将其还原。

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

请注意，在整个函数体中，**警告**杂注的最后一个设置将对整个函数有效。

## <a name="push-and-pop"></a>推送和弹出

**警告**杂注还支持以下语法，其中*n*表示警告等级（1到4）。

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragma `warning( push )` 存储每个警告的当前警告状态。 Pragma `warning( push, n )` 存储每个警告的当前状态，并将全局警告等级设置为*n*。

Pragma `warning( pop )` 弹出推送到堆栈上的最后一个警告状态。 对*推送*和*pop*之间的警告状态所做的任何更改都将被撤消。 请看以下示例：

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

在此代码的末尾， *pop*将每个警告的状态（包括4705、4706和4707）还原为它在代码开始时的状态。

当你编写标头文件时，可以使用*push*和*pop*来确保用户所做的警告状态更改不会阻止标头正确编译。 在标头开头使用*push* ，并在末尾使用*pop* 。 例如，如果你有一个在警告级别4不完全编译的标头，以下代码会将警告等级更改为3，然后在标头的末尾还原原始警告等级。

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

有关可帮助您禁止显示警告的编译器选项的详细信息，请参阅[/fi](../build/reference/fi-name-forced-include-file.md)和[/w](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
