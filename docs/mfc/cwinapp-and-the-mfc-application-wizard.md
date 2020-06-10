---
title: CWinApp 和 MFC 应用程序向导
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: f57b3b2b37a97093aa6d81b59a12c8cf023e3157
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622944"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 应用程序向导

当它创建主干应用程序时，MFC 应用程序向导将声明派生自[CWinApp](reference/cwinapp-class.md)的应用程序类。 MFC 应用程序向导还会生成一个包含以下项的实现文件：

- 应用程序类的消息映射。

- 空类构造函数。

- 声明类的一个和唯一一个对象的变量。

- 成员函数的标准实现 `InitInstance` 。

应用程序类放置在项目标题和主源文件中。 类的名称和创建的文件基于您在 MFC 应用程序向导中提供的项目名称。 查看这些类的代码的最简单方法是通过[类视图](/visualstudio/ide/viewing-the-structure-of-code)。

提供的标准实现和消息映射足以满足多种目的，但你可以根据需要进行修改。 这些实现中最值得注意的是 `InitInstance` 成员函数。 通常，您将向的框架实现添加代码 `InitInstance` 。

## <a name="see-also"></a>另请参阅

[CWinApp：应用程序类](cwinapp-the-application-class.md)<br/>
[可重写 CWinApp 成员函数](overridable-cwinapp-member-functions.md)<br/>
[特殊 CWinApp 服务](special-cwinapp-services.md)
