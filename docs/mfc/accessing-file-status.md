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
ms.openlocfilehash: 23c626940e700d3e9827ef6a7cf849d970e40d5d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619774"
---
# <a name="accessing-file-status"></a>访问文件状态

`CFile` 还支持获取文件状态，包括文件是否存在、创建和修改日期和时间、逻辑大小和路径。

### <a name="to-get-file-status"></a>获取文件状态

1. 使用[CFile](reference/cfile-class.md)类获取和设置有关文件的信息。 一个有用的应用程序是使用 `CFile` 静态成员函数**GetStatus**来确定文件是否存在。 如果指定的文件不存在，则**GetStatus**返回0。

因此，在打开文件时，可以使用**GetStatus**的结果来确定是否使用**CFile：： modeCreate**标志，如以下示例所示：

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

有关相关信息，请参阅[序列化](serialization-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[文件](files-in-mfc.md)
