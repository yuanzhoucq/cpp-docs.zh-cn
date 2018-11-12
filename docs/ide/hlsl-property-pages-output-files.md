---
title: HLSL 属性页：输出文件
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
ms.openlocfilehash: 96736b58eed280a0b4e91b9cb47cb53dc2e91cd4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513686"
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 属性页：输出文件

若要配置 HLSL 编译器 (fxc.exe) 的以下属性，请使用其“输出文件”属性。 有关如何访问 HLSL 文件夹中的“输出文件”属性页面，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

## <a name="uielement-list"></a>UIElement 列表

- **标头变量名称**

   指定用于编码 HLSL 对象代码的数组名称。 此数组包含在由 HLSL 编译器输出的头文件中。 头文件的名称由“头文件名”属性进行指定。

该属性对应于“/Vn [name]”命令行参数。

- **头文件名**

   指定由 HLSL 编译器输出的头文件名。 该标头包含编码到一个数组的 HLSL 对象代码。 数组的名称由“标头变量名”属性进行指定。

该属性对应于“/Fh [name]”命令行参数。

- **对象文件名**

   指定由 HLSL 编译器输出的对象文件名。 默认情况下，值为“$(OutDir)%(Filename).cso”。

该属性对应于“/Fo [name]”命令行参数。

- **汇编程序输出**

   **仅列出程序集 (/Fc)**：仅输出程序集语言语句。 **程序集代码和十六进制 (/Fx)**：输出程序集语言语句和相应十六进制的操作代码。 默认情况下，无列表输出。

- **汇编程序输出文件**

   指定由 HLSL 编译器输出的程序集列表文件名。

   该属性对应于“/Fo [name]”和“/Fx [name]”命令行参数。

## <a name="see-also"></a>请参阅

[“HLSL”属性页](../ide/hlsl-property-pages.md)<br>
[HLSL 属性页：常规](../ide/hlsl-property-pages-general.md)<br>
[HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)