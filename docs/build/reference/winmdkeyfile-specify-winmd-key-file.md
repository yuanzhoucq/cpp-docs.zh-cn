---
title: /WINMDKEYFILE（指定 winmd 密钥文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316452"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE（指定 winmd 密钥文件）

指定用来登录 Windows 运行时元数据 (.winmd) 文件的密钥或密钥对。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>备注

类似于[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)应用于.winmd 文件的链接器选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据密钥文件**框中，输入文件位置。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
