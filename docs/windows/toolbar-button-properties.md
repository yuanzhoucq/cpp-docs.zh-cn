---
title: 工具栏按钮属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e61ba7e8720c755ce26408826c56a5c1fc9d51e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890670"
---
# <a name="toolbar-button-properties"></a>工具栏按钮属性
工具栏按钮的属性是：  
  
|属性|描述|  
|--------------|-----------------|  
|**ID**|定义按钮的 ID。 下拉列表提供了常见**ID**名称。|  
|**宽度**|设置按钮的宽度。 建议 16 个像素。|  
|**高度**|设置按钮的高度。 请注意，一个按钮的高度更改的工具栏上的所有按钮的高度。 推荐使用 15 像素。|  
|**提示**|定义状态栏中显示的消息。 添加 \n 和名称添加到该工具栏按钮的工具提示。 有关详细信息，请参阅[创建工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|  
  
 **宽度**和**高度**应用于所有按钮。 用于创建工具栏位图具有的最大宽度为 2048年。 因此，如果将按钮宽度设置为 512，则可以只需四个按钮，并将宽度设置为 513，只能有三个按钮。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [更改工具栏按钮的属性](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

