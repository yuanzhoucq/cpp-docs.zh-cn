---
title: 指定的位置和大小的对话框 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
ms.openlocfilehash: 2c39cf5076ea38635268120da96fec6c82e23c47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524926"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>指定的位置和大小的对话框 （c + +）

位置和大小的 c + + 对话框中，并将位置和大小的控件，以对话框单元为单位测量。 当选择 Visual Studio 状态栏的右下角显示各个控件和对话框中的值。

有三个属性，您可以在设置[属性窗口](/visualstudio/ide/reference/properties-window)指定对话框将出现在屏幕上。 **Center**属性是一个布尔值; 如果将值设置为**True**，对话框中将始终显示在屏幕的中心。 如果设置为**False**，然后，可以设置**XPos**并**YPos**属性来显式定义在屏幕上将显示此对话框。 位置属性是从查看区域，该常数定义为左上角的偏移量的值`{X=0, Y=0}`。 位置也基于**Absolute Align**属性： 如果**True**，坐标是相对于屏幕; 如果**False**，坐标都相对于对话框所有者的窗口。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)