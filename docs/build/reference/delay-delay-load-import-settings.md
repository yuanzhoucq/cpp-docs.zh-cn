---
title: /DELAY（延迟加载导入设置）
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492999"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY（延迟加载导入设置）

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>备注

/DELAY 选项控制 Dll 的[延迟加载](linker-support-for-delay-loaded-dlls.md):

- UNLOAD 限定符通知延迟加载 Helper 函数支持 DLL 的显式卸载。 导入地址表 (IAT) 被重置为其原始形式，从而使 IAT 指针无效并导致它们被覆盖。

   如果未选择 "卸载", 任何对[FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md)的调用将失败。

- NOBIND 限定符通知链接器不要在最终图像中包含可绑定的 IAT。 默认值是为延迟加载的 DLL 创建可绑定的 IAT。 无法静态绑定生成的图像。 （可以在执行之前静态绑定包含可绑定 IAT 的图像。）请参阅[/BIND](bind.md)。

   如果 DLL 已绑定, 则 helper 函数将尝试使用绑定的信息, 而不是对每个引用的导入调用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 。 如果时间戳或首选地址与加载的 DLL 的时间戳或首选地址不匹配，则 Helper 函数将假定绑定的 IAT 已经过期并继续执行，就像绑定的 IAT 不存在一样。

   NOBIND 导致程序图像比较大，但是可以加快 DLL 的加载时间。 如果从不打算绑定 DLL，则 NOBIND 将禁止生成绑定的 IAT。

若要指定要延迟加载的 Dll, 请使用[/DELAYLOAD](delayload-delay-load-import.md)选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关信息, 请[参阅C++在 Visual Studio 中设置编译器和生成属性](../working-with-project-properties.md)。

1. 展开 "**配置属性**"、"**链接器**", 然后选择 "**高级**"。

1. 修改 "**延迟加载的 DLL** " 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
