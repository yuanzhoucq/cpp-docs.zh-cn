---
title: "警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- warning_CPP
- vc-pragma.warning
dev_langs:
- C++
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b295eb94732a50db977d240dbcd9b4d80e105b3c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="warning-pragma"></a>警告杂注
启用编译器警告消息的行为的选择性修改。  
  
## <a name="syntax"></a>语法  
  
```
#pragma warning(   
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )  
#pragma warning( push[ ,n ] )  
#pragma warning( pop )  
```  
  
## <a name="remarks"></a>备注  
以下警告说明符参数可用。  
  
|警告说明符|含义|  
|------------------------|-------------|  
|`1, 2, 3, 4`|将给定级别应用于指定的警告。 这也会启用默认情况下处于关闭状态的指定警告。|  
|`default`|将警告行为重置为其默认值。 这也会启用默认情况下处于关闭状态的指定警告。 警告将在其默认存档级别生成。<br /><br /> 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|`disable`|不发出指定的警告消息。|  
|`error`|将指定警告报告为错误。|  
|`once`|只显示指定消息一次。|  
|`suppress`|将杂注的当前状态推送到堆栈上，禁用下一行的指定警告，然后弹出警告堆栈，从而重置杂注状态。|  
  
 以下代码语句演示了 `warning-number-list` 参数可包含多个警告编号，并演示了可在同一杂注指令中指定多个 `warning-specifier` 参数。  
  
```cpp  
#pragma warning( disable : 4507 34; once : 4385; error : 164 )  
```  
  
 这在功能上等效于以下代码。  
  
```cpp  
// Disable warning messages 4507 and 4034.  
#pragma warning( disable : 4507 34 )  
  
// Issue warning 4385 only once.  
#pragma warning( once : 4385 )  
  
// Report warning 4164 as an error.  
#pragma warning( error : 164 )  
```  
  
 编译器将 4000 添加到 0 和 999 之间的任何警告编号。  
  
 对于范围 4700-4999 内的警告编号（与代码生成相关联），在编译器遇到函数的左大括号时生效的警告状态将对函数的其余部分生效。 在函数中使用 `warning` 杂注更改编号大于 4699 的警告的状态只会在函数末尾之后生效。 以下示例演示如何正确放置 `warning` 杂注来禁用代码生成警告消息然后还原该消息。  
  
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
  
 请注意，在整个函数体中，`warning` 杂注的最后一个设置将对整个函数有效。  
  
## <a name="push-and-pop"></a>推送和弹出  
 `warning`杂注还支持以下语法，其中`n`表示警告等级 (1 到 4)。  
  
 `#pragma warning( push [ , n ] )`  
  
 `#pragma warning( pop )`  
   
 杂注`warning( push )`存储每个警告的当前警告状态。 杂注`warning( push, n )`存储每个警告的当前状态并将全局警告级别设置为`n`。  
  
 杂注`warning( pop )`最后一个的警告状态推送到堆栈中弹出。 在 `push` 和 `pop` 之间对警告状态所做的任何更改都将被撤消。 请看以下示例：  
  
```cpp  
#pragma warning( push )  
#pragma warning( disable : 4705 )  
#pragma warning( disable : 4706 )  
#pragma warning( disable : 4707 )  
// Some code  
#pragma warning( pop )   
```  
  
 在此代码的末尾，`pop` 会将每个警告（包括 4705、4706 和 4707）的状态还原为其在代码开头的状态。  
  
 编写标头文件时，您可以使用 `push` 和 `pop` 来确保用户所做的警告状态更改不会阻止标头进行正确的编译。 请在标头的开头使用 `push`，并在标头的末尾使用 `pop`。 例如，如果你具有不在警告等级 4 完全编译的标头，以下代码会将警告等级更改为 3，然后在标头的末尾还原原始警告等级。  
  
```cpp  
#pragma warning( push, 3 )  
// Declarations/definitions  
#pragma warning( pop )   
```  
  
 有关帮助你的选项禁止显示的编译器警告，请参阅[/FI](../build/reference/fi-name-forced-include-file.md)和[/w](../build/reference/compiler-option-warning-level.md)。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)