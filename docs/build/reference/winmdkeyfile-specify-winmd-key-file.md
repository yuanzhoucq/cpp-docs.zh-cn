---
title: /WINMDKEYFILE（指定 winmd 密钥文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 076533278bb9b8ec2838cfb719bcb4df1784b258
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436785"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE（指定 winmd 密钥文件）

指定用来登录 Windows 运行时元数据 (.winmd) 文件的密钥或密钥对。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>备注

类似于[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)应用于.winmd 文件的链接器选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据密钥文件**框中，输入文件位置。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)