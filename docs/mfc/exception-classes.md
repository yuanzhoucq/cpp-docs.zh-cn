---
title: 异常类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.exception
dev_langs:
- C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ce4085d0f5f2dcc73d126d04b7560ef8360ffd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="exception-classes"></a>异常类
类库提供基于类 `CException` 的异常处理机制。 应用程序框架将在其代码中使用异常；你也可在你自己的代码中使用异常。 有关详细信息，请参阅文章[异常](../mfc/exception-handling-in-mfc.md)。 您可从 `CException` 派生自己的异常类型。  
  
 MFC 提供了您可从其派生自己的异常的异常类以及其支持的所有异常的异常类。  
  
 [CException](../mfc/reference/cexception-class.md)  
 异常的基类。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 存档异常。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 DAO 数据库操作失败导致的异常。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 ODBC 数据库处理失败导致的异常。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 面向文件的异常。  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 内存不足异常。  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 使用不支持的功能导致的异常。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 OLE 处理失败导致的异常。 此类将由容器和服务器使用。  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 自动化期间出错导致的异常。 自动化异常由自动化服务器引发，由自动化客户端捕获。  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 Windows 资源加载失败导致的异常。  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 用于停止用户启动的操作的异常。 通常，用户在此异常引发前已收到有关问题的通知。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

