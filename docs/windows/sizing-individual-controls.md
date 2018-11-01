---
title: 调整单个控件的大小
ms.date: 11/04/2016
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: 32a43e6cf8eff9f1da8eb08294834982c6755f52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466880"
---
# <a name="sizing-individual-controls"></a>调整单个控件的大小

使用大小调整句柄来调整控件的大小。 仅当鼠标指针置于调整大小控点时，它将改变形状以指示可以在其中调整控件的说明操作。 活动的调整大小控点都是可靠;如果大小调整句柄是空心，控件不能沿该轴的大小调整。

此外可以通过将控件与参考线或边距，对齐更改控件的大小，或通过将移动一个对齐控件和参考线彼此。

### <a name="to-size-a-control"></a>若要调整控件的大小

1. 选择的控件。

2. 拖动调整大小控点，若要更改控件的大小：

   - 在顶部和边的调整大小控点更改水平或垂直大小。

   - 角的调整大小控点更改水平和垂直大小。

   > [!TIP]
   > 可以通过按下一次调整控件一个对话框单元 （dlu） 地**Shift**密钥和使用**向右箭头**并**向下箭头**密钥。

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自动调整大小以适应其中的文本的控件

1. 选择**内容调整大小**从**格式**菜单。

\- 或 -

- 右键单击该控件，然后选择**内容调整大小**从快捷菜单。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)