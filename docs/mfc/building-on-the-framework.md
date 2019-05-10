---
title: 基于框架生成
ms.date: 11/04/2016
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
ms.openlocfilehash: 989aecdfafc0d57bfb28874ee84dbf40f8fefc30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385331"
---
# <a name="building-on-the-framework"></a>基于框架生成

在对应用程序配置 MFC 框架中的角色是提供特定于应用程序的源代码并通过定义消息和命令响应的连接组件。 使用C++语言和标准版C++技术为您自己的特定于应用程序的类派生这些类库提供的并可以重写和增加基类的行为。

在相关主题中下, 表描述了您通常将执行的操作和您的职责与框架的职责的一般顺序：

- [生成应用程序时使用 Framework 的序列](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [OLE 应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [ActiveX 控件的创建操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [数据库应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)

大多数情况下，你可以按照这些表作为一系列的步骤创建 MFC 应用程序，尽管某些步骤的替代选项。 例如，大多数应用程序使用一种类型的视图类中可用的多个类型。

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
