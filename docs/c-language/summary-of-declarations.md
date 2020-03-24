---
title: 声明摘要
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170431"
---
# <a name="summary-of-declarations"></a>声明摘要

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*声明-说明符* *属性-seq*<sub>opt</sub> *init-声明符-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*存储类说明符* *声明-说明符*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型说明符* *声明-说明符*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型限定符* *声明-说明符*<sub>opt</sub>

*属性-seq* ：&nbsp;&nbsp;&nbsp;&nbsp;/\* \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*特性* *属性-seq*<sub>opt</sub>

*属性*：&nbsp;&nbsp;中的一个 &nbsp;&nbsp;/\* \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;init-declarator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-声明符-list* **，** *init-声明符*

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;declarator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*声明符* **=** 用于标量*初始化 /\** \*    /

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;auto<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;__declspec /\* \*/ **（** *decl* **）** &nbsp;

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;void<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;__int8 /\*** \*/<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;__int16 /\*** \*/<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;__int32 /\*** \*/<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;__int64 /\*** \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;typedef-name

*type-qualifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;const<br/>
&nbsp;&nbsp;&nbsp;&nbsp;volatile

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指针*<sub>可选</sub>*直接声明符*

*direct-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identifier<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **（** *声明符* **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接声明符* **[** *常量表达式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接声明符* **（** *参数类型列表* **）**  /\* \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接声明符* **（** *标识符列表*<sub>opt</sub> **）**  /\* 过时样式的声明符 \*/

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *类型限定符-列表*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *类型限定符-列表*<sub>opt</sub> *指针*

parameter-type-list：&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* 参数列表 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;parameter-list<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*参数列表* **，...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;parameter-declaration<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*参数-列表* **、** *参数声明*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;type-qualifier<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型限定符-列表* *类型-限定符*

*enum-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**枚举***标识符*<sub>opt</sub> **{** *枚举器* **}**<br/>
&nbsp;**枚举***标识符*&nbsp;&nbsp;&nbsp;

*enumerator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*的枚举器列表* **、** *枚举器*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*枚举常量* **=** *常数表达式*

*enumeration-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identifier

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*结构或联合* *标识符*<sub>opt</sub> **{** *struct-list* **}**<br/>
&nbsp;*结构或联合* *标识符*&nbsp;&nbsp;&nbsp;

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;struct<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;*结构声明列表* *的 &nbsp;* &nbsp;&nbsp;

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*说明符--限定符* *列表* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型说明符* *说明符-限定符-列表*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型限定符* *说明符-限定符-列表*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*结构声明符* *结构声明符-列表* **，** *struct 声明符*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;declarator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*类型说明符* *declarator*<sub>opt</sub> **：** *常量表达式*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*声明-说明符* *声明符* /\* 命名声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*声明说明符* *抽象-声明符*<sub>opt</sub> /\* 匿名声明符 \*/

identifier-list：/\*用于旧式声明符\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identifier<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*标识符-列表* **，** *标识符*

abstract-declarator：/\* 用于匿名声明符 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;pointer<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指针*<sub>可选</sub>*直接抽象-声明符*

*direct-abstract-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **（** *抽象-声明符* **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接抽象声明符*<sub>opt</sub> **[** *常量表达式*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接抽象声明符*<sub>opt</sub> **（** *参数类型列表*<sub>opt</sub> **）**

*initializer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;assignment-expression<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *初始值设定项列表* **}**  /\* \*聚合初始化/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *初始值设定项列表* **，}**

*initializer-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;initializer<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*初始值设定项列表* **，** *初始值设定项*

*type-name*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*说明符-列表* *抽象声明符*<sub>opt</sub>

*typedef-name*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identifier

*decl*&nbsp;&nbsp;&nbsp;&nbsp;/\* 特定于 Microsoft 的 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decl* *扩展 decl-* 修饰符

*decl-修饰符*：&nbsp;&nbsp;&nbsp;&nbsp;/\* \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>另请参阅

[调用约定](../cpp/calling-conventions.md)<br/>
[短语结构语法](../c-language/phrase-structure-grammar.md)<br/>
[已过时调用约定](../cpp/obsolete-calling-conventions.md)
