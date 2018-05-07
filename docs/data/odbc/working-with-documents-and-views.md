---
title: 使用文档和视图 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 71750507d6b3c6cf14a721971d809347f8adfd3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-documents-and-views"></a>使用文档和视图
Microsoft 基础类 (MFC) 库为它的许多功能依赖于文档/视图体系结构。 通常情况下，文档存储你的数据然后查看显示在框架窗口的客户端区域内和管理与数据的用户交互。 该视图与该文档以获取更新的数据进行通信。 你可以使用数据库类，与框架或不它。  
  
 有关在框架中使用数据库类的详细信息，请参阅[MFC： 结合文档和视图使用数据库类](../../data/mfc-using-database-classes-with-documents-and-views.md)。  
  
 默认情况下，MFC 应用程序向导创建主干应用程序没有数据库支持。 但是，你可以选择选项以包括最少的数据库支持或更完整的基于窗体的支持。 有关应用程序向导选项的详细信息，请参阅[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 此外，你可以使用数据库类而不使用完整的文档/视图体系结构。 有关详细信息，请参阅[MFC： 使用数据库类不结合文档和视图](../../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)