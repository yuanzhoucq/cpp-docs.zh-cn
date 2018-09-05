---
title: 指定属性页 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ISpecifyPropertyPages
dev_langs:
- C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b93a93b545d03875167ccd641fa3e0867c371a8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759367"
---
# <a name="specifying-property-pages"></a>指定属性页

创建 ActiveX 控件时，通常想要将它与可用于设置控件的属性的属性页相关联。 控制容器使用`ISpecifyPropertyPages`接口以找出哪些属性页可以用于设置控件的属性。 你将需要您的控件上实现此接口。

若要实现`ISpecifyPropertyPages`使用 ATL，执行以下步骤：

1. 从类派生[ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)。

2. 为添加一个条目`ISpecifyPropertyPages`到您的类的 COM 映射。

3. 添加[PROP_PAGE](reference/property-map-macros.md#prop_page)属性映射为每个页面与控件关联的条目。

> [!NOTE]
>  生成标准控件使用时[ATL 控件向导](../atl/reference/atl-control-wizard.md)，只需将 PROP_PAGE 项添加到属性映射。 该向导生成所需的代码执行其他步骤。

功能良好的容器将显示指定的属性页，在属性映射中 PROP_PAGE 项的顺序相同。 通常情况下，则应将标准属性页项后项自定义属性映射中页，以便用户先看到特定于控件的页。

## <a name="example"></a>示例

下面的类的一个日历控件使用`ISpecifyPropertyPages`告知容器可以使用自定义日期页和常用颜色页设置其属性的接口。

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>请参阅

[属性页](../atl/atl-com-property-pages.md)   
[ATLPages 示例](../visual-cpp-samples.md)

