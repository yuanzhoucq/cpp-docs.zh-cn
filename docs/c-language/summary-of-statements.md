---
title: 语句摘要
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 122c79b53a8af8a384097dec51a14746a090b1cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220790"
---
# <a name="summary-of-statements"></a>语句摘要

*statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*compound-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*selection-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteration-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-statement* /\* Microsoft-specific \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-statement* /\* Microsoft-specific \*/

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`goto`  identifier  ;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**continue ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`return` expression<sub>opt</sub> ;

compound-statement  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

declaration-list  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

statement-list  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

expression-statement  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *expression*  **)**  *statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`do`  statement  while (  expression  ) ;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (**  *expression*<sub>opt</sub> **;** *expression*<sub>opt</sub> **;** *expression*<sub>opt</sub> **)** *statement*

*selection-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (**  *expression*  **)**  *statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;if (  expression  )  statement  `else`  statement<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**switch (**  *expression*  **)**  *statement*

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*  **:**  *statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`case`  constant-expression  :  statement<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default :**  *statement*

*try-except-statement*:   /\* Microsoft-specific \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try**  *compound-statement* **__except (**  *expression*  **)**  *compound-statement*

*try-finally-statement*:   /\* Microsoft-specific \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;__try  compound-statement `__finally`  compound-statement

## <a name="see-also"></a>请参阅

[短语结构语法](../c-language/phrase-structure-grammar.md)
