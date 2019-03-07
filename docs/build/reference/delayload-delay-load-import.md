---
title: /DELAYLOAD（延迟加载导入）
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: aa8cc5a565b4af625a1ee85f67ca1c82e065486b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416275"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD（延迟加载导入）

> **/DELAYLOAD:**_dll 名称_

## <a name="parameters"></a>参数

*dllname*<br/>
想要延迟加载的 DLL 的名称。

## <a name="remarks"></a>备注

/DELAYLOAD 选项导致 `dllname` 指定的 DLL 只能在程序第一次调用该 DLL 中的函数时加载。 有关详细信息，请参阅[被延迟加载 Dll 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)。 你可以根据需要多次使用此选项，以便指定已选的多个 DLL。 当链接你的程序时，你必须使用 Delayimp.lib，或者也可以实现你自己的延迟加载 Helper 函数。

[/延迟](../../build/reference/delay-delay-load-import-settings.md)选项指定绑定和加载的每个延迟加载的 DLL 的选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 在中**链接器**文件夹，选择**输入**属性页。

1. 修改**延迟加载的 Dll**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
