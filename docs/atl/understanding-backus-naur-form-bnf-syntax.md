---
title: ATL 注册器和巴科斯-诺尔范式 (BNF) 语法
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168704"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>了解巴科斯-诺尔范式 (BNF) 语法

本主题使用 BNF 语法来描述 ATL 注册器使用的脚本，将使用下表中所示的表示法。

|约定/符号|含义|
|------------------------|-------------|
|::=|等效|
|&#124;|OR|
|X+|一个或多个 X。|
|\[X]|X 是可选的。 可选的分隔符由 \[] 表示。|
|任何粗体文本****|字符串文本。|
|任何斜体文本**|如何构造字符串文本。|

如上表所示，注册器脚本使用字符串文本。 这些值是必须出现在脚本中的实际文本。 下表介绍了在 ATL 注册器脚本中使用的字符串文本。

|字符串文本|操作|
|--------------------|------------|
|**ForceRemove**|完全删除下一个项（如果存在），然后重新创建它。|
|**NoRemove**|取消注册期间不会删除下一个项。|
|**初始值**|指定 `<Key Name>` 实际上是命名值。|
|**删除**|注册期间删除下一个项。|
|**些**|指定下一个值是字符串 (REG_SZ)。|
|**2-d**|指定下一个值是 DWORD (REG_DWORD)。|
|**年**|指定下一个值是多字符串 (REG_MULTI_SZ)。|
|**b**|指定下一个值是二进制值 (REG_BINARY)。|

## <a name="bnf-syntax-examples"></a>BNF 语法示例

以下是一些语法示例，有助于了解表示法和字符串文本在 ATL 注册器脚本中的工作原理。

### <a name="syntax-example-1"></a>语法示例 1

> \<注册表表达式>：： = \<Add Key>

指定 `registry expression` 等效于 `Add Key`。

### <a name="syntax-example-2"></a>语法示例 2

> \<注册表表达式>：： = \<Add Key> |\<删除密钥>

指定 `registry expression` 等效于 `Add Key` 或 `Delete Key`。

### <a name="syntax-example-3"></a>语法示例 3

> \<项名称>：： = '\<字母数字>+ '

`Key Name`指定等效于一个或多个`AlphaNumeric`值。

### <a name="syntax-example-4"></a>语法示例 4

> \<Add key>：： = [**ForceRemove** | **NoRemove** | **val**]\<key Name>

指定 `Add Key` 等效于 `Key Name`，并且指定字符串文本 `ForceRemove`、`NoRemove` 和 `val` 是可选的。

### <a name="syntax-example-5"></a>语法示例 5

> \<字母数字>：： =*任意字符 NOT NULL，即 ASCII 0*

指定 `AlphaNumeric` 等效于任何非 NULL 字符。

### <a name="syntax-example-6"></a>语法示例 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

指定项名称 `testmulti` 是由 `String 1` 和 `String 2` 组成的多字符串值。

### <a name="syntax-example-7"></a>语法示例 7

```rgs
val 'testhex' = d '&H55'
```

指定项名称 `testhex` 是设置为十六进制的 55（十进制为 85）的 DWORD 值。 请注意，此格式符合 Visual Basic 规范中找到的 &H 表示法****。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
