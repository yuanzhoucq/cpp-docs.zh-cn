---
title: ODBC 和数据库类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e179bf7570ba2ce53369d59c836e8accf91e8de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057930"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和数据库类

MFC ODBC 数据库类封装了您将通常使自己的成员中的函数的 ODBC API 函数调用[CDatabase](../../mfc/reference/cdatabase-class.md)并[CRecordset](../../mfc/reference/crecordset-class.md)类。 例如，复杂的 ODBC 调用序列、 返回的记录到存储位置、 处理错误条件，以及其他操作的绑定是为您管理的数据库类。 因此，使用相当简单的类接口来处理通过记录集对象的记录。

> [!NOTE]
>  ODBC 数据源是可通过 MFC ODBC 类，如本主题中所述或 MFC 数据访问对象 (DAO) 类的访问。

尽管数据库类封装了 ODBC 功能，但它们不提供 ODBC API 函数的一对一映射。 数据库类提供更高级别的抽象，建模后找到 Microsoft Access 和 Microsoft Visual Basic 中的数据访问对象。 有关详细信息，请参阅[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。

## <a name="see-also"></a>请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)