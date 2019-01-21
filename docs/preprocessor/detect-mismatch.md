---
title: detect_mismatch
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: fb6f147f1591f010298e84cb28f05b40dafaeb63
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417624"
---
# <a name="detectmismatch"></a>detect_mismatch
将记录放在一个对象中。 链接器将检查这些记录中的潜在不匹配项。

## <a name="syntax"></a>语法

```
#pragma detect_mismatch("name", "value")
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
