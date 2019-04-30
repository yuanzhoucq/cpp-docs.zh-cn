---
title: 访问文件状态
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 26c263b2d7e4e0243444925cb9416cb337dcd79d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392955"
---
# <a name="accessing-file-status"></a>访问文件状态

`CFile` 还支持获取文件状态，包括文件是否存在、创建和修改日期和时间、逻辑大小和路径。

### <a name="to-get-file-status"></a>获取文件状态

1. 使用[CFile](../mfc/reference/cfile-class.md)类来获取和设置文件的相关信息。 一个有用的应用程序是使用`CFile`静态成员函数**GetStatus**来确定文件是否存在。 **GetStatus**如果指定的文件不存在，则返回 0。

因此，可以使用的结果**GetStatus**以确定是否使用**cfile:: Modecreate**标志时打开的文件，如以下示例所示：

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

有关相关信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>请参阅

[文件](../mfc/files-in-mfc.md)
