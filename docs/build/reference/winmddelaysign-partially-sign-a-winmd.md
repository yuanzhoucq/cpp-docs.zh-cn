---
title: -WINMDDELAYSIGN （部分对 winmd 的签名） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b31f6ae5baf9aadbb40b4b45f532b344b6b2e037
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723848"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN（对 winmd 进行部分签名）

通过将公钥部分放在 Windows 运行时元数据 (.winmd) 文件中来启用该文件的部分签名。

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>备注

类似于[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)应用于.winmd 文件的链接器选项。 使用**放**如果你想要将仅将公钥放在.winmd 文件。 默认情况下，链接器的作用如同 **/winmddelaysign: no**指定; 即，不会签署 winmd 文件。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据延迟签名**下拉列表框中，选择所需的选项。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)