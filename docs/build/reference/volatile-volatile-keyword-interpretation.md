---
title: -volatile （volatile 关键字解释） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccd36c5edaaab8577e5f278b25b51ce69e0633f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile（volatile 关键字解释）

指定如何[易失性](../../cpp/volatile-cpp.md)关键字将被解释。

## <a name="syntax"></a>语法

> **/volatile:**{**iso**|**ms**}  

## <a name="arguments"></a>自变量

**/volatile:iso**  
选择严格`volatile`按照 ISO 标准 c + + 语言定义的语义。 获取/释放语义不保证在易失性访问。 如果编译器面向 ARM，这是默认解释`volatile`。

**/volatile: ms**  
选择 Microsoft 扩展`volatile`语义，从而添加排序保障超出 ISO 标准 c + + 语言的内存。 获取/释放语义保证在易失性访问。 但是，此选项还会强制编译器生成可能会显著增加开销，ARM 和其他弱内存排序体系结构的硬件内存屏障。 如果编译器面向 ARM 除任何平台，这是默认解释`volatile`。

## <a name="remarks"></a>备注

我们强烈建议你使用 **/volatile:iso**以及显式同步基元和编译器内部函数在处理跨线程共享的内存时。 有关详细信息，请参阅[易失性](../../cpp/volatile-cpp.md)。

如果你将现有代码，或更改项目的中间此选项，它可能会很有用，若要启用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)以标识受语义上的不同的代码位置。

没有任何`#pragma`等效以控制此选项。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>若要设置 /volatile 编译器选项在 Visual Studio 中

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 在**其他选项**框中，添加 **/volatile:iso**或 **/volatile: ms** ，然后选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[volatile](../../cpp/volatile-cpp.md)  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
