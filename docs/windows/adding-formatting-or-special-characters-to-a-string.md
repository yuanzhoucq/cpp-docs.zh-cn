---
title: 将格式设置或特殊字符添加到字符串资源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bf67723f516e0c5b1bf9931d7f53d36907fca86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313385"
---
# <a name="adding-formatting-or-special-characters-to-a-string-resource-c"></a>将格式设置或特殊字符添加到字符串资源 （c + +）

### <a name="to-add-formatting-or-special-characters-to-a-string"></a>若要为字符串添加格式设置或特殊字符

1. 通过双击中对应的图标打开字符串表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 选择你想要修改的字符串。

3. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，添加任何标准的转义序列中的文本到下列**标题**框，然后按**Enter**。

   |若要获取此信息|键入这|
   |-----------------|---------------|
   |换行|\n|
   |回车|\r|
   |Tab|\t|
   |反斜杠 (\\)|\\\|
   |ASCII 字符|\ddd （八进制表示法）|
   |警报 （响铃）|\a|

> [!NOTE]
> **字符串**编辑器不支持转义 ASCI 字符的完整集。 您只能使用上面所列。

有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\))。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[字符串编辑器](../windows/string-editor.md)  