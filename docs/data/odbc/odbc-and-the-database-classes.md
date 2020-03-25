---
title: ODBC 和数据库类
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213152"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和数据库类

MFC ODBC 数据库类封装了通常在[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)类的成员函数中执行的 ODBC API 函数调用。 例如，复杂的 ODBC 调用序列、将返回的记录绑定到存储位置、处理错误条件以及其他操作由数据库类管理。 因此，您可以使用一个相当简单的类接口通过 recordset 对象操作记录。

> [!NOTE]
>  ODBC 数据源可通过 MFC ODBC 类访问，如本主题中所述，或通过 MFC 数据访问对象（DAO）类访问。

尽管数据库类封装了 ODBC 功能，但它们并不提供 ODBC API 函数的一对一映射。 数据库类提供了更高级别的抽象，它在 Microsoft Access 和 Microsoft Visual Basic 中找到的数据访问对象之后建模。 有关详细信息，请参阅[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
