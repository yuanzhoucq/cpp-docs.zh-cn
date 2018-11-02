---
title: /ENTRY（入口点符号）
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 21e17d9ec9c4b145af8909730e5f799de9b72ce2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615522"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY（入口点符号）

```
/ENTRY:function
```

## <a name="arguments"></a>自变量

*函数*<br/>
一个函数，指定用户定义的开始地址为.exe 文件或 DLL。

## <a name="remarks"></a>备注

/ENTRY 选项指定为.exe 文件或 DLL 的起始地址的入口点函数。

该函数必须定义为使用`__stdcall`调用约定。 参数和返回值取决于如果程序是一个控制台应用程序、 windows 应用程序或 DLL。 建议您让链接器设置，以便 C 运行时库正确初始化，并执行的静态对象的 c + + 构造函数的入口点。

默认情况下的起始地址是 C 运行时库中的函数名。 链接器来选择该程序的特性根据下表中所示。

|功能名称|默认值为|
|-------------------|-----------------|
|**mainCRTStartup** (或**wmainCRTStartup**)|使用 /subsystem: console; 的应用程序调用`main`(或`wmain`)|
|**WinMainCRTStartup** (或**wWinMainCRTStartup**)|使用 /SUBSYSTEM 的应用程序：**WINDOWS**; 调用`WinMain`(或`wWinMain`)，必须对其进行定义以使用 `__stdcall`|
|**_DllMainCRTStartup**|DLL;调用`DllMain`如果存在，其必须进行定义以使用 `__stdcall`|

如果[/DLL](../../build/reference/dll-build-a-dll.md)或[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)未指定选项、 链接器会选择取决于是否的子系统和入口点`main`或`WinMain`定义。

函数`main`， `WinMain`，和`DllMain`是三种形式的用户定义入口点。

/ENTRY 到指定的函数创建托管的映像时，必须具有的签名 (LPVOID *var1*，DWORD *var2*，LPVOID *var3*)。

了解如何定义您自己`DllMain`入口点，请参阅[Dll 和 Visual c + + 运行时库行为](../../build/run-time-library-behavior.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**高级**属性页。

1. 修改**入口点**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)