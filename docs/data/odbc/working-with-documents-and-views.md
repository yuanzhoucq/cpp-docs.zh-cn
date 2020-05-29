---
title: 使用文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
ms.openlocfilehash: 452fb010705e808aabd2ad42d1a0b6ba1c5921ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212363"
---
# <a name="working-with-documents-and-views"></a>使用文档和视图

Microsoft 基础类（MFC）库依赖于其中许多功能的文档/视图体系结构。 通常，文档存储数据，视图在框架窗口的工作区中显示，并管理用户与数据的交互。 视图与文档通信以获取和更新数据。 可以将数据库类与框架一起使用，也可以不使用。

有关在框架中使用数据库类的详细信息，请参阅[MFC：将数据库类与文档和视图结合使用](../../data/mfc-using-database-classes-with-documents-and-views.md)。

默认情况下，MFC 应用程序向导创建没有数据库支持的框架应用程序。 不过，您可以选择选项以包括最小数据库支持或更完整的基于窗体的支持。 有关应用程序向导选项的详细信息，请参阅[MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)。

你还可以使用数据库类，而无需使用完整的文档/视图体系结构。 有关详细信息，请参阅[MFC：不使用文档和视图的数据库类](../../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
