---
title: 链接器工具警告 LNK4224 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdffdf3469cc3a0e5d41b0504b882513d44b63c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703982"
---
# <a name="linker-tools-warning-lnk4224"></a>链接器工具警告 LNK4224

> *选项*不再受支持; 被忽略

## <a name="remarks"></a>备注

指定并忽略无效、 过时的链接器选项。

例如，如果 /comment 指令出现在出现 LNK4224 可以。 obj。/Comment 指令将通过添加[注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)杂注时，使用不推荐使用的 exestr 选项。 使用 dumpbin [/所有](../../build/reference/all.md)若要查看的.obj 文件中的链接器指令。

如果可能，请修改.obj 的源和移除杂注。 如果不要忽略此警告，则可能使用编译.executable **/clr: pure**将未按预期运行。 **/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

## <a name="example"></a>示例

下面的示例生成 LNK4224。

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```