---
title: 链接器工具警告 LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465320"
---
# <a name="linker-tools-warning-lnk4224"></a>链接器工具警告 LNK4224

> *选项*不再受支持; 已忽略

## <a name="remarks"></a>备注

指定并忽略无效、 已过时的链接器选项。

例如，如果 /comment 指令出现在发生 LNK4224 可以。 目标/Comment 指令将通过添加[注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)杂注，使用不推荐使用的 exestr 选项。 使用 dumpbin [/all](../../build/reference/all.md)在.obj 文件中查看链接器指令。

如果可能，请修改为.obj 源并删除杂注。 如果不要忽略此警告，就可以使用编译.executable **/clr: pure**不会按预期方式运行。 **/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

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