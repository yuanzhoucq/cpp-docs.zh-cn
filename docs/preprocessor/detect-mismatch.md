---
title: detect_mismatch |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55d7c3b81b3b8c43fb9024f2a58c27028950b144
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064168"
---
# <a name="detectmismatch"></a>detect_mismatch
将记录放在一个对象中。 链接器将检查这些记录中的潜在不匹配项。

## <a name="syntax"></a>语法

```
#pragma detect_mismatch( "name", "value"))
```

## <a name="remarks"></a>备注

链接项目时，如果项目包含 `LNK2038` 相同但 `name` 不同的两个对象，则链接器将引发 `value` 错误。 使用此杂注可防止链接中存在不一致的对象文件。

名称和值都是字符串，它们遵循关于转义字符和串联的字符串规则。 区分大小写，不能包含逗号、 等号、 引号中，或**null**字符。

## <a name="example"></a>示例

此示例将创建版本标签相同但版本号不同的两个文件。

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

如果使用命令行 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 编译这两个文件，则会收到错误 `LNK2038`。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)