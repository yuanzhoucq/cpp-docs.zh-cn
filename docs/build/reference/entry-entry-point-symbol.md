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
ms.openlocfilehash: 80833980b64e8fdd2a2f57b2dc40eb21c784b6f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232698"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY（入口点符号）

```
/ENTRY:function
```

## <a name="arguments"></a>参数

*函数*<br/>
一个函数，该函数指定 .exe 文件或 DLL 的用户定义的起始地址。

## <a name="remarks"></a>备注

/ENTRY 选项将入口点函数指定为 .exe 文件或 DLL 的起始地址。

必须定义函数才能使用 **`__stdcall`** 调用约定。 如果程序为控制台应用程序、windows 应用程序或 DLL，则参数和返回值将依赖于。 建议使链接器设置入口点，以便正确初始化 C 运行时库，并执行静态对象的 c + + 构造函数。

默认情况下，起始地址是 C 运行库中的函数名称。 链接器将根据程序的属性选择该属性，如下表所示。

|函数名称|默认值|
|-------------------|-----------------|
|**mainCRTStartup** （或**wmainCRTStartup**）|使用/SUBSYSTEM：控制台的应用程序;调用 `main` （或 `wmain` ）|
|**WinMainCRTStartup** （或**wWinMainCRTStartup**）|使用/SUBSYSTEM 的应用程序：**WINDOWS**;调用 `WinMain` （或 `wWinMain` ），必须将其定义为使用**`__stdcall`**|
|**_DllMainCRTStartup**|DLL;`DllMain`如果它存在，则调用它，它必须定义为使用**`__stdcall`**|

如果未指定[/DLL](dll-build-a-dll.md)或[/SUBSYSTEM](subsystem-specify-subsystem.md)选项，则链接器将根据是否定义了或来选择子系统和入口点 `main` `WinMain` 。

函数 `main` 、 `WinMain` 和 `DllMain` 是用户定义入口点的三个窗体。

创建托管图像时，指定给/ENTRY 的函数必须具有签名（LPVOID *var1*、DWORD *var2*、LPVOID *var3*）。

有关如何定义自己的 `DllMain` 入口点的信息，请参阅[dll 和 Visual C++ 运行时库行为](../run-time-library-behavior.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击“链接器”文件夹****。

1. 单击 "**高级**" 属性页。

1. 修改 "**入口点**" 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
