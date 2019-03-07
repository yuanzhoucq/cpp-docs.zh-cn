---
title: /SWAPRUN（将链接器输出加载到交换文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
ms.openlocfilehash: 085be83bf73288871c71bef00378ddd494cd6f8d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424868"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN（将链接器输出加载到交换文件）

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>备注

/SWAPRUN 选项告知操作系统首次复制到链接器输出到交换文件，然后从那里运行映像。 这是 Windows NT 4.0 （及更高版本） 功能。

如果指定 NET，则操作系统会首先将二进制文件映像从网络复制到交换文件，并从那里加载它。 此选项可用于在网络上运行应用程序。 当指定 CD 时，操作系统将可移动磁盘上的映像复制到一个页面文件，然后将其加载。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改以下属性之一：

   - **从 CD 交换运行**

   - **从网络交换运行**

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 属性。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
