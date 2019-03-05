---
title: 异常:检查异常内容
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: f6f9bca6f6b7ca9d104cb492c760ab89f7163afd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259381"
---
# <a name="exceptions-examining-exception-contents"></a>异常:检查异常内容

尽管**捕获**块的参数可以是几乎任何数据类型、 MFC 函数引发异常的类型派生自类`CException`。 若要捕获由 MFC 函数引发的异常，然后编写**捕获**块其参数是一个指针，到`CException`对象 (或一个派生自`CException`，如`CMemoryException`)。 根据异常的确切类型，可以检查要收集相关信息的具体原因的异常的异常对象的数据成员。

例如，`CFileException`类型具有`m_cause`数据成员，其中包含指定文件异常的原因的枚举的类型。 可能的一些示例都返回值是否`CFileException::fileNotFound`和`CFileException::readOnly`。

下面的示例演示如何检查的内容`CFileException`。 可以类似方式查看其他异常类型。

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

有关详细信息，请参阅[异常：释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)和[异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
