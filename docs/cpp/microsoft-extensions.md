---
title: Microsoft 扩展
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301768"
---
# <a name="microsoft-extensions"></a>Microsoft 扩展

*asm 语句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm**  *assembly-instruction* **;**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {**  *assembly-instruction-list*  **} ;**<sub>opt</sub>

*程序集指令列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;**<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** *assembly-instruction-list* **;**<sub>opt</sub>

*ms 修饰符列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms-modifier* *ms-modifier-list*<sub>opt</sub>

*ms 修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*based-modifier*

*基于修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *基于类型* **)**

*基于类型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*name*