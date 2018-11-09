---
title: C 字符串文本
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: bd8b49645e34224cbea7e801f197bfbcbc012915
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635600"
---
# <a name="c-string-literals"></a>C 字符串文本

“字符串文本”是封闭在双引号 (" ") 内的源字符集中的字符序列。 字符串用于表示可一起构成以 null 结尾的字符串的字符序列。 必须在宽字符串文本前添加字母 L 作为前缀。

## <a name="syntax"></a>语法

string-literal：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s-char-sequence*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

s-char-sequence：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

s-char：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;除双引号 (")、反斜杠 (\\) 或者换行符以外的任何源字符集成员<br/>

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>备注

以下示例是一个简单的字符串：

```C
char *amessage = "This is a string literal.";
```

在[转义序列](../c-language/escape-sequences.md)表中列出的所有转义码在字符串文本中均有效。 若要表示字符串文本中的双引号，请使用转义序列 \\"。 可在不使用转义序列的情况下表示单引号 (')。 反斜杠 (\\) 在字符串中出现时必须后跟另一个反斜杠 (\\\\)。 当反斜杠出现在行的末尾时，始终解释为行继续符。

## <a name="see-also"></a>请参阅

[C 的元素](../c-language/elements-of-c.md)
