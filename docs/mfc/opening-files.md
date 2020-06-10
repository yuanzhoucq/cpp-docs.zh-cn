---
title: 打开文件
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622153"
---
# <a name="opening-files"></a>打开文件

在 MFC 中，最常见的文件打开方式是一个两阶段过程。

#### <a name="to-open-a-file"></a>打开文件

1. 创建文件对象，无需指定路径或权限标志。

   通常通过在堆栈帧上声明[CFile](reference/cfile-class.md)变量来创建文件对象。

1. 为文件对象调用[Open](reference/cfile-class.md#open)成员函数，同时提供路径和权限标志。

   如果成功打开文件，则 `Open` 的返回值不为零；否则如果指定文件未能打开，则为 0。 `Open` 成员函数的原型如下所示：

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   打开标志指定您需要文件具有哪些权限（如只读）。 可能的标志值定义为 `CFile` 类中的枚举常数，因此它们具有“`CFile::`”的资格，如在 `CFile::modeRead` 中一样。 如果需要创建文件，则请使用 `CFile::modeCreate` 标志。

以下示例演示如何创建具有读/写权限的新文件（替换路径相同的任何之前的文件）：

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> 此示例将创建并打开文件。 如果出现问题，则 `Open` 调用将在其最后一个参数中返回 `CFileException` 对象，如下所示。 跟踪宏将同时打印文件名和指示失败原因的代码。 如果您需要更详细的错误报告，则可以调用 `AfxThrowFileException` 函数。

## <a name="see-also"></a>另请参阅

[CFile 类](reference/cfile-class.md)<br/>
[CFile：： Open](reference/cfile-class.md#open)<br/>
[文件](files-in-mfc.md)
