---
title: 要保留的自变量
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 918be9d281f1cb12c27c6c2f5dd834e4af137179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313553"
---
# <a name="arguments-to-main"></a>要保留的自变量

**ANSI 2.1.2.2.1**：main 参数的语义

在 Microsoft C 中，程序启动时调用的函数称为 **main**。 没有针对 **main** 声明的原型，可以用零个、两个或三个参数对其进行定义：

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

上面第三行（其中，**main** 接受三个参数）是 Microsoft ANSI C 标准扩展。 第三个参数 (**envp**) 是指向环境变量的指针的数组。 **envp** 数组以 null 指针终止。 有关 **main** 和 **envp** 的详细信息，请参阅 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)。

变量 **argc** 从不保留负值。

字符串数组以包含 null 指针的 **argv[argc]** 结束。

**argv** 数组的所有元素都是指向字符串的指针。

未使用命令行参数调用的程序将接收 **argc** 的值 1，因为可执行文件的名称将置于 **argv[0]** 内。 （在 3.0 之前的 MS-DOS 版本中，可执行文件名不可用。 字母“C”将置于 **argv[0]** 中。）**argv[1]** 通过 **argv[argc – 1]** 指向的字符串表示程序参数。

参数 **arg** 和 **argv** 是可修改的，并在程序启动与程序终止之间保留最后存储的值。

## <a name="see-also"></a>请参阅

[环境](../c-language/environment.md)
