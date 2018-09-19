---
title: ATL 注册器和巴科斯-诺尔构成 (BNF) 语法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e615068580bcc9078959cc6cdd7831d05b5a4acd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020870"
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>了解巴科斯-诺尔范式 (BNF) 语法

使用 ATL 注册器的脚本使用 BNF 语法，使用下表中所示的表示法本主题所述。

|约定/符号|含义|
|------------------------|-------------|
|::=|等效|
|&#124;|或|
|X +|一个或多个 Xs。|
|[X]|X 是可选的。 由表示可选分隔符\[]。|
|任何**粗体**文本|字符串文字。|
|任何*斜体*文本|如何构造的字符串文字。|

上表中所示，注册器脚本将使用字符串文本。 这些值是必须出现在脚本中的实际文本。 下表描述了在 ATL 注册器脚本中使用的字符串文本。

|字符串文本|操作|
|--------------------|------------|
|**ForceRemove**|完全删除下一个键 （如果存在），然后重新创建它。|
|**NoRemove**|不会在注销期间删除的下一个键。|
|**val**|指定`<Key Name>`是实际的命名的值。|
|**删除**|删除在注册过程的下一个键。|
|**秒**|指定下一个值，是一个字符串 (REG_SZ)。|
|**d**|指定下一个值是 DWORD (REG_DWORD)。|
|**m**|指定下一个值是多字符串 (REG_MULTI_SZ)。|
|**b**|指定下一个值是一个二进制值 (REG_BINARY)。|

## <a name="bnf-syntax-examples"></a>BNF 语法示例

以下是几个语法示例，以帮助您了解表示法和字符串文本中的 ATL 注册器脚本的工作方式。

### <a name="syntax-example-1"></a>语法示例 1

```
<registry expression> ::= <Add Key>
```

指定的`registry expression`等效于`Add Key`。

### <a name="syntax-example-2"></a>语法示例 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

指定的`registry expression`等效于任一`Add Key`或`Delete Key`。

### <a name="syntax-example-3"></a>语法示例 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

指定的`Key Name`相当于一个或多个`AlphaNumerics`。

### <a name="syntax-example-4"></a>语法示例 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

指定的`Add Key`等效于`Key Name`，和的字符串文本， `ForceRemove`， `NoRemove`，和`val`，都是可选的。

### <a name="syntax-example-5"></a>语法示例 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

指定`AlphaNumeric`等效到任何非 NULL 字符。

### <a name="syntax-example-6"></a>语法示例 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

指定的密钥名称`testmulti`由多字符串值组成`String 1`和`String 2`。

### <a name="syntax-example-7"></a>语法示例 7

```
val 'testhex' = d '&H55'
```

指定的密钥名称`testhex`DWORD 值设置为十六进制 55 (十进制 85)。 请注意此格式符合 **& H**作为表示法在 Visual Basic 规范中找到。

## <a name="see-also"></a>请参阅

[创建注册器脚本](../atl/creating-registrar-scripts.md)

