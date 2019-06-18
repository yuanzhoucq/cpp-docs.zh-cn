---
title: /link（将选项传递到链接器）
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 37743e855c933b6236b5e7a837db257f332a3037
ms.sourcegitcommit: bbaf65f8ed1af12828b38f8eacd24f934ac0e538
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "67155781"
---
# <a name="link-pass-options-to-linker"></a>/link（将选项传递到链接器）

将一个或多个链接器选项传递给链接器。

## <a name="syntax"></a>语法

> **/link** *linker-options*

## <a name="arguments"></a>自变量

*linker-options*<br/>
链接器选项或要传递给链接器选项。

## <a name="remarks"></a>备注

**/Link**选项以及与之链接器选项必须出现在任何文件的名称和 CL 选项之后。 是之间需要空格 **/link**和任何链接器选项。 有关详细信息，请参阅[MSVC 链接器引用](linking.md)。

## <a name="example"></a>示例

此示例命令行编译*hello.cpp*并将其链接到现有的对象文件*there.obj*。然后将其传递额外 **/VERSION**到链接器命令：

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

通常情况下，IDE 将发送单独的命令来编译和链接你的代码。 在项目属性页中，可以设置链接器选项。

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器**文件夹。

1. 修改一个或多个属性。 选择“确定”以保存更改  。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 不能以编程方式更改此编译器选项。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
