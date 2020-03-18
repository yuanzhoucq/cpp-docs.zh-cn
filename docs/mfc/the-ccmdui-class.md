---
title: CCmdUI 类
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447144"
---
# <a name="the-ccmdui-class"></a>CCmdUI 类

在框架将更新命令传送到其处理程序时，框架会传递给处理程序一个指向 `CCmdUI` 对象（或 `CCmdUI` 派生的类的对象）的指针。 此对象表示生成命令的菜单项或工具栏按钮或其他用户界面对象。 更新处理程序通过指针调用 `CCmdUI` 结构的成员函数来更新用户界面对象。 例如，以下是一个用于“全部清除”菜单项的更新处理程序：

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

此处理程序通过访问菜单项来调用对象的 `Enable` 成员函数。 `Enable` 使该项可供使用。

## <a name="see-also"></a>另请参阅

[如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)
