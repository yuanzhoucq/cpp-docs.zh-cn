---
title: Microsoft 扩展 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752234"
---
# <a name="microsoft-extensions"></a>Microsoft 扩展

*asm 语句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***程序集指令* **;**<sub>选择  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***程序集指令列表***};**<sub>选择    </sub>

*程序集指令列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;**<sub>选择</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;***程序集指令列表* **;**<sub>选择</sub>

*ms 修饰符列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms 修饰符* *ms 修饰符列表*<sub>选择</sub>

*ms 修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*基于修饰符*

*基于修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *基于类型* **)**

*基于类型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名称*