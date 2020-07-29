---
title: /volatile（volatile 关键字解释）
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 7c2c1cd477b424f56e66bd9246e7bde76ad06120
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223780"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile（volatile 关键字解释）

指定如何解释[volatile](../../cpp/volatile-cpp.md)关键字。

## <a name="syntax"></a>语法

> **/volatile：**{**iso** | **ms**}

## <a name="arguments"></a>参数

**/volatile： iso**<br/>
选择 **`volatile`** ISO 标准 c + + 语言定义的严格语义。 在易失性访问上不保证获取/释放语义。 如果编译器面向 ARM，则这是的默认解释 **`volatile`** 。

**/volatile： ms**<br/>
选择 Microsoft 扩展 **`volatile`** 语义，该语义添加超出 ISO 标准 c + + 语言的内存排序保证。 获取/释放语义可保证可变访问。 但是，此选项还强制编译器生成硬件内存障碍，这可能会增加 ARM 和其他弱内存排序体系结构的开销。 如果编译器以除 ARM 以外的任何平台为目标，则这是的默认解释 **`volatile`** 。

## <a name="remarks"></a>备注

当处理跨线程共享的内存时，强烈建议使用 **/volatile： iso**以及显式同步基元和编译器内部函数。 有关详细信息，请参阅[volatile](../../cpp/volatile-cpp.md)。

如果在项目中间移植现有代码或更改此选项，则启用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)可能会很有帮助，以便识别受语义差异影响的代码位置。

没有 `#pragma` 等效于控制此选项。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置/volatile 编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中，添加 **/volatile： iso**或 **/volatile： Ms** ，然后选择 **"确定" 或 "** **应用**" 保存更改。

## <a name="see-also"></a>另请参阅

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
