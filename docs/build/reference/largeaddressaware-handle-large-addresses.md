---
title: /LARGEADDRESSAWARE（处理大地址）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 81a560ebf083e2f93d9bb514fc401186291d7f41
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808113"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE（处理大地址）

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>备注

/LARGEADDRESSAWARE 选项通知链接器应用程序可以处理大于 2 千兆字节的地址。 在 64 位编译器中，默认情况下启用此选项。 在 32 位编译器中，如果 /LARGEADDRESSAWARE 否则未指定链接器行上启用 /largeaddressaware: no。

如果应用程序已链接使用 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](headers.md)将显示该结果的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**启用大地址**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
