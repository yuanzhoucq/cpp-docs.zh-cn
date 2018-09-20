---
title: MFC 自定义 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 640d6726623e8fb6d563153823f449f7caefcf30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384996"
---
# <a name="customization-for-mfc"></a>MFC 自定义

本主题提供了有关自定义 MFC 应用程序的提示。

## <a name="general-customizations"></a>常规自定义

您可以将应用程序状态保存并加载到注册表。 如果启用此选项，则应用程序将从注册表加载其初始状态。 如果更改应用程序的初始停靠布局，则必须清除应用程序的注册表数据。 否则，注册表中的数据将覆盖您对初始布局的所有更改。

## <a name="class-specific-customizations"></a>特定于类的自定义

可以在下列主题中找到其他自定义提示：

- [CBasePane 类](../mfc/reference/cbasepane-class.md)

- [CDockablePane 类](../mfc/reference/cdockablepane-class.md)

- [CDockingManager 类](../mfc/reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl 类](../mfc/reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>其他自定义提示

[键盘和鼠标自定义](../mfc/keyboard-and-mouse-customization.md)

[用户定义的工具](../mfc/user-defined-tools.md)

## <a name="see-also"></a>请参阅

[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)<br/>
[自定义对安全有何影响](../mfc/security-implications-of-customization.md)

