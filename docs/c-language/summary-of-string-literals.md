---
title: 字符串文本的摘要
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: 72f5aa6405ae97bfb6141db737affa0c3aca2a65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648118"
---
# <a name="summary-of-string-literals"></a>字符串文本的摘要

string-literal：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *s-char-sequence*<sub>opt</sub> **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *s-char-sequence*sub>opt</sub> **'**

s-char-sequence：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

s-char：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;除双引号 (")、反斜杠 (\\) 或换行符 escape-sequence 之外的源字符集的任何成员

## <a name="see-also"></a>请参阅

[词法语法](../c-language/lexical-grammar.md)