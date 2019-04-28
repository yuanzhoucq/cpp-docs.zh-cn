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
ms.openlocfilehash: e92b470b7b5e76b39371f333cbbda150e7f6e8c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273348"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD（延迟加载导入）

> **/DELAYLOAD:**_dll 名称_

## <a name="parameters"></a>参数

*dllname*<br/>
想要延迟加载的 DLL 的名称。

## <a name="remarks"></a>备注

/DELAYLOAD 选项导致 `dllname` 指定的 DLL 只能在程序第一次调用该 DLL 中的函数时加载。 有关详细信息，请参阅[被延迟加载 Dll 的链接器支持](linker-support-for-delay-loaded-dlls.md)。 你可以根据需要多次使用此选项，以便指定已选的多个 DLL。 当链接你的程序时，你必须使用 Delayimp.lib，或者也可以实现你自己的延迟加载 Helper 函数。

[/延迟](delay-delay-load-import-settings.md)选项指定绑定和加载的每个延迟加载的 DLL 的选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 在中**链接器**文件夹，选择**输入**属性页。

1. 修改**延迟加载的 Dll**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
