---
title: 使用文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
ms.openlocfilehash: 030ac53b924e4746bcd79e712313ce2f30b4198c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023979"
---
# <a name="working-with-documents-and-views"></a>使用文档和视图

Microsoft 基础类 (MFC) 库依赖于它的许多功能的文档/视图体系结构。 通常情况下，存储数据的文档和视图的框架窗口的工作区内显示和管理用户与数据交互。 该视图与要获取和更新数据的文档进行通信。 使用框架或没有它，可以使用数据库类。

有关在框架中使用数据库类的详细信息，请参阅[MFC:结合文档和视图使用数据库类](../../data/mfc-using-database-classes-with-documents-and-views.md)。

默认情况下，MFC 应用程序向导创建主干应用程序不支持数据库。 但是，你可以选择选项以包括最少的数据库支持或更完整的基于窗体的支持。 有关应用程序向导选项的详细信息，请参阅[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)。

此外可以在不使用完整的文档/视图体系结构的情况下使用数据库类。 有关详细信息，请参阅[MFC:使用不含文档和视图的类](../../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)