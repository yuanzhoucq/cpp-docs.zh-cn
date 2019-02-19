---
title: C 扩展的存储类特性
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 9b0c8b60dab3229d5d5c162f7bafc959fa2558f0
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146952"
---
# <a name="c-extended-storage-class-attributes"></a>C 扩展的存储类特性

**Microsoft 专用**

有关本主题的更多最新信息可以在 [__declspec（C++ 参考）](../cpp/declspec.md)下找到。

扩展的特性语法简化并标准化了特定于 Microsoft 的 C 语言扩展。 使用扩展的特性语法的存储类特性包括 thread、naked、dllimport 和 dllexport。

用于指定存储类信息的扩展特性语法使用 __declspec 关键字，这指定给定类型的实例将与特定于 Microsoft 的存储类特性（thread、naked、dllimport 或 dllexport）一起存储。 其他存储类修饰符的示例包括 static 和 extern 关键字。 但是，这些关键字是 ANSI C 标准的一部分，因此未涵盖在扩展的特性语法中。

## <a name="syntax"></a>语法

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)** /\* Microsoft 专用 \*/

extended-decl-modifier-seq：&nbsp;&nbsp;&nbsp;&nbsp;/\*Microsoft 专用 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

extended-decl-modifier：&nbsp;&nbsp;&nbsp;&nbsp;/\*Microsoft 专用 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

空格可分隔声明修饰符。 请注意，extended-decl-modifier-seq 可以为空；在此情况下，__declspec 不起作用。

thread、naked、dllimport 和 dllexport 存储类特性仅为它们应用于的数据或函数的声明的属性；它们不重新定义函数自身的类型特性。 thread 特性只影响数据。 naked 特性仅影响函数。 dllimport 和 dllexport 特性影响函数和数据。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
