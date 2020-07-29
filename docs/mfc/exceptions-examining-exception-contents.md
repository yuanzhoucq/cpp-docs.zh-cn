---
title: 异常：检查异常内容
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 7500db2a29f9d4ccef37b9265f5f2968c2d07993
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217943"
---
# <a name="exceptions-examining-exception-contents"></a>异常：检查异常内容

尽管 **`catch`** 块的参数可以是几乎任何数据类型，但 MFC 函数会引发从类派生的类型的异常 `CException` 。 若要捕获 MFC 函数引发的异常，请编写一个块，该 **`catch`** 块的参数是指向对象的指针 `CException` （或派生自的对象 `CException` ，如 `CMemoryException` ）。 根据异常的具体类型，可以检查 exception 对象的数据成员，以收集有关异常的特定原因的信息。

例如， `CFileException` 类型具有 `m_cause` 数据成员，该成员包含指定文件异常原因的枚举类型。 可能的返回值的一些示例包括 `CFileException::fileNotFound` 和 `CFileException::readOnly` 。

下面的示例演示如何检查的内容 `CFileException` 。 可以按类似方式检查其他异常类型。

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

有关详细信息，请参阅[异常：释放异常](exceptions-freeing-objects-in-exceptions.md)和[异常对象：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
