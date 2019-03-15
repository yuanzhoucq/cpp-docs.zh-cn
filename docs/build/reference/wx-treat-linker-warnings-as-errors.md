---
title: /WX（将链接器警告视为错误）
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: b4b29ed364d39c5f105dded703b8530c08db35e6
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822085"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX（将链接器警告视为错误）

```
/WX[:NO]
```

## <a name="remarks"></a>备注

不 /wx 链接器生成警告会生成任何输出文件。

它类似于 **/WX**编译器 (请参阅[/w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）](compiler-option-warning-level.md)有关详细信息)。 但是，指定 **/WX**为编译并不意味着 **/WX**也将实际上在链接阶段; 必须显式指定 **/WX**的每个工具。

默认情况下 **/WX**不起作用。 若要将链接器警告视为错误，请指定 **/WX**。 **/WX:NO**相当于将不指定 **/WX**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 点击“命令行”  属性页。

1. 该选项键入**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
