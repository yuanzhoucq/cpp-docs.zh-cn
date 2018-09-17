---
title: -LARGEADDRESSAWARE （处理大地址） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a68b18f912d7e6ca0f0f642c85e8439be0e5b67
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726319"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE（处理大地址）

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>备注

/LARGEADDRESSAWARE 选项通知链接器应用程序可以处理大于 2 千兆字节的地址。 在 64 位编译器中，默认情况下启用此选项。 在 32 位编译器中，如果 /LARGEADDRESSAWARE 否则未指定链接器行上启用 /largeaddressaware: no。

如果应用程序已链接使用 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)将显示该结果的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**启用大地址**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)