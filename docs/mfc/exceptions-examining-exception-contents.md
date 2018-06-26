---
title: 异常： 检查异常内容 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c7453b92ce14fbbcd20ea0f9a8bd8a7a2b5b6d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932229"
---
# <a name="exceptions-examining-exception-contents"></a>异常：检查异常内容
尽管**捕获**块的自变量可以是几乎任何数据类型，则 MFC 函数引发派生自类类型的异常`CException`。 若要捕获 MFC 函数引发的异常，然后，你编写**捕获**块其参数为指针到`CException`对象 (或从派生的对象`CException`，如`CMemoryException`)。 根据异常的具体类型，你可以检查要收集的异常信息的具体原因的异常对象的数据成员。  
  
 例如，`CFileException`类型具有`m_cause`数据成员，其中包含指定文件异常原因的枚举的类型。 可能的一些示例返回的值为`CFileException::fileNotFound`和`CFileException::readOnly`。  
  
 下面的示例演示如何检查的内容`CFileException`。 可以类似方式查看其他异常类型。  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 有关详细信息，请参阅[异常： 释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)和[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

