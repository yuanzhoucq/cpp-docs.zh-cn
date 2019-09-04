---
title: detect_mismatch 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 6e247b3f251bce47710a3380fb295597314a3bd8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222392"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch 杂注

将记录放在一个对象中。 链接器将检查这些记录中的潜在不匹配项。

## <a name="syntax"></a>语法

> **#pragma detect_mismatch (** "*name*" **,** "*value*" **)**

## <a name="remarks"></a>备注

链接项目时, 如果项目包含两个具有相同*名称*的对象, 但每个对象具有不同的*值*, 则链接器将引发[LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md)错误。 使用此杂注可防止链接中存在不一致的对象文件。

*名称*和*值*都是字符串文本, 并遵循有关转义字符和串联的字符串文字的规则。 它们是区分大小写的, 不能包含逗号、等号、引号或**null**字符。

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

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
