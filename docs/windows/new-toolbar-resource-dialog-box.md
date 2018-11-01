---
title: 新建工具栏资源对话框 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
ms.openlocfilehash: 7c45daeb2c07426918f1a636f4230c1c07026ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595918"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>新建工具栏资源对话框 （c + +）

**新建工具栏资源**对话框允许您指定的宽度和高度的要添加到 c + + 项目中的工具栏资源按钮。 默认值为 16 × 15 像素。

用于创建工具栏位图有 2048年的最大宽度。 因此，如果您设置**按钮宽度**为 512，只能有四个按钮。 如果将宽度设置为 513，您只能有三个按钮。

### <a name="button-width"></a>按钮宽度

提供空间以输入将从位图资源转换为工具栏资源的工具栏按钮的宽度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。

### <a name="button-height"></a>按钮高度

提供空间以输入将从位图资源转换为工具栏资源的工具栏按钮的高度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[工具栏按钮属性](../windows/toolbar-button-properties.md)<br/>
[将位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)