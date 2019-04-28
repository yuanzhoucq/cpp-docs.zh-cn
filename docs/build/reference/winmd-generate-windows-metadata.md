---
title: /WINMD（生成 Windows 元数据）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 93db20d14d3477734e35d33111246f9459310b90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317154"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD（生成 Windows 元数据）

启用 Windows 运行时元数据 (.winmd) 文件的生成。

> **/WINMD**\[**:**{**NO**\|**ONLY**}]

## <a name="arguments"></a>自变量

**/WINMD**<br/>
通用 Windows 平台应用的默认设置。 链接器生成二进制可执行文件和 .winmd 元数据文件。

**/WINMD:NO**<br/>
链接器仅生成二进制可执行文件，但不生成 .winmd 文件。

**/WINMD:ONLY**<br/>
链接器仅生成 .winmd 文件，但不生成二进制可执行文件。

## <a name="remarks"></a>备注

**/WINMD**链接器选项使用适用于 UWP 应用和 Windows 运行时组件，以控制创建 Windows 运行时元数据 (.winmd) 文件。 .Winmd 文件是一种类型的 DLL，其中包含元数据，Windows 运行时类型，并在运行时组件，这些类型的实现的情况下。 元数据遵循[ECMA-335](http://www.ecma-international.org/publications/standards/Ecma-335.htm)标准。

默认情况下，输出文件名称采用以下格式*binaryname*.winmd。 若要指定不同的文件名称，请使用[/WINMDFILE](winmdfile-specify-winmd-file.md)选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **Windows 元数据**属性页。

1. 在中**生成 Windows 元数据**下拉列表框中，选择所需的选项。

## <a name="see-also"></a>请参阅

[演练：创建一个简单的 Windows 运行时组件并从 JavaScript 调用它](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Microsoft 接口定义语言 3.0 简介](/uwp/midl-3/intro)<br/>
[/WINMDFILE（指定 winmd 文件）](winmdfile-specify-winmd-file.md)<br/>
[/WINMDFILE（指定 winmd 密钥文件）](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER（指定密钥容器）](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN（对 winmd 进行部分签名）](winmddelaysign-partially-sign-a-winmd.md)<br/>
[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
