---
title: -volatile （volatile 关键字解释） |Microsoft Docs
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
ms.openlocfilehash: 4204d602d1390bf30080a800174426513faf0467
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723627"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile（volatile 关键字解释）

指定如何[易失性](../../cpp/volatile-cpp.md)关键字将被解释。

## <a name="syntax"></a>语法

> **/volatile:**{**iso**|**ms**}

## <a name="arguments"></a>自变量

**/volatile: iso**<br/>
选择严格`volatile`ISO 标准 c + + 语言定义的语义。 获取/释放语义无法保证可变访问。 如果编译器面向 ARM，这是默认的解释`volatile`。

**/volatile: ms**<br/>
选择 Microsoft 扩展`volatile`添加内存顺序调整保证超出 ISO 标准 c + + 语言的语义。 获取/释放语义可保证可变访问。 但是，此选项还强制编译器生成硬件内存障碍，这可能会在 ARM 和其他弱内存命令体系结构上添加很大的开销。 如果编译器面向除 ARM 之外的任何平台，这是默认值解释`volatile`。

## <a name="remarks"></a>备注

我们强烈建议你使用 **/volatile: iso**以及显式同步基元和编译器内部函数在处理跨线程共享的内存时。 有关详细信息，请参阅[易失性](../../cpp/volatile-cpp.md)。

如果将现有代码或更改项目中间此选项，它可能是启用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)来标识受语义上差异影响的代码位置。

没有任何`#pragma`相当于控制此选项。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /volatile 编译器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 在中**其他选项**框中，添加 **/volatile: iso**或 **/volatile: ms** ，然后选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[volatile](../../cpp/volatile-cpp.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
