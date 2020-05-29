---
title: ODBC 和数据库类
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320066"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和数据库类

MFC ODBC 数据库类封装了您通常在[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)类的成员函数中编写的 ODBC API 函数调用。 例如，复杂的 ODBC 调用序列、返回的记录绑定到存储位置、处理错误条件以及其他操作由数据库类为您管理。 因此，您可以使用更简单的类接口通过记录集对象操作记录。

> [!NOTE]
> ODBC 数据源可通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 （DAO） 类访问。

尽管数据库类封装了 ODBC 功能，但它们不提供 ODBC API 函数的一对一映射。 数据库类提供更高级别的抽象，以 Microsoft Access 和 Microsoft Visual Basic 中找到的数据访问对象建模。 有关详细信息，请参阅[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
