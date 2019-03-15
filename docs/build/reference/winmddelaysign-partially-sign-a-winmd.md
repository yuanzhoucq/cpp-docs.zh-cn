---
title: /WINMDDELAYSIGN（对 winmd 进行部分签名）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 5e6eab3fbc40543b634f03da826d3bd3477b9623
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57421451"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN（对 winmd 进行部分签名）

通过将公钥部分放在 Windows 运行时元数据 (.winmd) 文件中来启用该文件的部分签名。

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>备注

类似于[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)应用于.winmd 文件的链接器选项。 使用**放**如果你想要将仅将公钥放在.winmd 文件。 默认情况下，链接器的作用如同 **/winmddelaysign: no**指定; 即，不会签署 winmd 文件。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据延迟签名**下拉列表框中，选择所需的选项。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
