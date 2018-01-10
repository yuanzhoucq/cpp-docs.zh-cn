---
title: "TN032: MFC 异常机制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.exceptions
dev_langs: C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf82d4b158cedd2d8f6916dfb01d26db6c62d83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032：MFC 异常机制
以前版本的 Visual c + + 不支持标准 c + + 异常机制，和 MFC 中提供的宏**TRY/CATCH/THROW** ，只能改为使用。 此版本的 Visual C++ 完全支持 C++ 异常。 本说明包含以前的宏的高级实现详细信息，包括如何自动清理基于堆栈的对象。 由于 C++ 异常默认支持堆栈展开，此技术说明不再是必需的。  
  
 请参阅[异常： 使用 MFC 宏和 c + + 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)有关 MFC 宏和新的 c + + 关键字之间的差异的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

