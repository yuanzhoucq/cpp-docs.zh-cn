---
title: CL 调用链接器
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: 1f9bb466ae89b8e3491b027a98b28935e7c8b523
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440179"
---
# <a name="cl-invokes-the-linker"></a>CL 调用链接器

除非使用/c 选项，否则 CL 将在编译后自动调用链接器。 CL 将编译过程中创建的 .obj 文件的名称和命令行上指定的任何其他文件的名称传递到链接器。 链接器使用 LINK 环境变量中列出的选项。 您可以使用/link 选项来指定 CL 命令行上的链接器选项。 遵循/link 选项的选项会替代链接环境变量中的选项。 下表中的选项取消链接。

|选项|说明|
|------------|-----------------|
|/c|编译但不链接|
|/E，/EP，/P|无需编译或链接的预处理|
|/Zg|生成函数原型|
|/Zs|检查语法|

有关链接的详细信息，请参阅[MSVC 链接器选项](linker-options.md)。

## <a name="example"></a>示例

假设你要编译三个 C 源文件： MOD1、和 MOD2。 每个文件都包含对在其他文件中定义的函数的调用：

- MAIN .c 调用函数 `func1` 在 MOD1 中，将函数 `func2` 在 MOD2 中。

- MOD1 调用 `printf_s` 和 `scanf_s`标准库函数。

- MOD2 调用名为 `myline` 和 `mycircle`的图形函数，它们是在名为 MYGRAPH 的库中定义的。

若要生成此程序，请通过以下命令行进行编译：

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL 首先编译 C 源文件，并创建对象文件 MAIN .obj、MOD1 和 MOD2。编译器将标准库的名称放在每个 .obj 文件中。 有关更多详细信息，请参阅[使用运行时库](md-mt-ld-use-run-time-library.md)。

CL 将 .obj 文件的名称以及名称 MYGRAPH 传递到链接器。 链接器解析外部引用，如下所示：

1. 在 MAIN .obj 中，使用 MOD1 中的定义解析对 `func1` 的引用;使用 MOD2 中的定义解析对 `func2` 的引用。

1. 在 MOD1 中，将使用链接器在 MOD1 中找到的名称库中的定义解析对 `printf_s` 和 `scanf_s` 的引用。

1. 在 MOD2 中，将使用 MYGRAPH 中的定义解析对 `myline` 和 `mycircle` 的引用。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[设置编译器选项](compiler-command-line-syntax.md)
