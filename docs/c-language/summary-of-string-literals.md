---
title: 字符串文本的摘要
ms.date: 11/04/2016
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
ms.openlocfilehash: bc235a26849c284d8b46216606d40d07452e2237
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149682"
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
