---
title: /CLRIMAGETYPE（指定 CLR 映像的类型）
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: c4cdb9a9ac3376762d6aa40fd4c13abbdc7b5487
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461628"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE（指定 CLR 映像的类型）

链接的图像中设置的 CLR 映像类型。

## <a name="syntax"></a>语法

> **/CLRIMAGETYPE:**{**IJW**|**纯**|**安全**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>备注

链接器接受本机对象以及 MSIL 对象编译的使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 **/Clr: pure**并 **/clr: safe**编译器选项已弃用 Visual Studio 2015 和 Visual Studio 2017 中不受支持。 同一版本中传递混合对象时，结果输出文件的可验证性级别默认等于输入模块的最低可验证性级别。 例如，如果传递本机映像和混合的模式映像 (使用编译的 **/clr**)，结果映像将为混合的模式映像。

可以使用 **/CLRIMAGETYPE**指定较低级别的可验证性，如果您的需要。

有关如何确定文件的 CLR 映像类型的信息，请参阅 [/CLRHEADER](../../build/reference/clrheader.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**CLR 映像类型**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
