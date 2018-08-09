---
title: 更改多个字符串的 Caption 属性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- String editor, changing properties of multiple strings
- strings [C++], changing caption property of multiple
- string editing, string tables
- string tables, changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2372230726530bb0d9bbf8eb4e187cd55c203711
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649092"
---
# <a name="changing-the-caption-property-of-multiple-strings"></a>更改多个字符串的 Caption 属性
以下过程演示如何更改多个字符串的 caption 属性。  
  
### <a name="to-change-the-caption-property-of-multiple-strings"></a>若要更改多个字符串的 caption 属性  
  
1.  通过双击中对应的图标打开字符串表[资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  选择你想要通过按下更改的字符串**Ctrl**单击每个键。  
  
3.  在中[属性窗口](/visualstudio/ide/reference/properties-window)，键入你想要更改的属性的新值。  
  
4.  按 **Enter**。  
  
 有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[演练： 使用 for Localization with ASP.NET 资源](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [字符串编辑器](../windows/string-editor.md)   