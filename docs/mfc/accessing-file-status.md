---
title: "访问文件状态 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff93028c192a735ec75721d3dfdb9929a35edad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-file-status"></a>访问文件状态
`CFile` 还支持获取文件状态，包括文件是否存在、创建和修改日期和时间、逻辑大小和路径。  
  
### <a name="to-get-file-status"></a>获取文件状态  
  
1.  使用[CFile](../mfc/reference/cfile-class.md)类获取和设置文件的相关信息。 一个有用的应用程序是使用`CFile`静态成员函数**GetStatus**以确定文件是否存在。 **GetStatus**如果指定的文件不存在，则返回 0。  
  
 因此，您可使用的结果**GetStatus**来确定是否使用**CFile::modeCreate**标志打开的文件时，如下面的示例所示：  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 有关相关信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [文件](../mfc/files-in-mfc.md)

