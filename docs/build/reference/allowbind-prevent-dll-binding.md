---
title: -ALLOWBIND （禁止 DLL 绑定） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 536fc4f43cf227491ecae53cb5960e42ff79e081
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713617"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND（禁止 DLL 绑定）

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>备注

/ALLOWBIND:NO 在 DLL 的标头中设置一个位，向 Bind.exe 指示不允许绑定图像。 如果 DLL 已经进行数字签名（绑定使签名无效），可能不需要绑定 DLL。

您可以编辑 /ALLOWBIND 功能的现有 DLL [/ALLOWBIND](../../build/reference/allowbind.md) EDITBIN 实用工具的选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开**配置属性**，**链接器**，然后选择**命令行**。

1. 输入`/ALLOWBIND:NO`成**其他选项**。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>
[执行 bindimage 操作函数](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx 函数](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)