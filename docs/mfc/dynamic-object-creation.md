---
title: 动态对象创建 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5763e3f0f3ee5a0e58ac20fe9f637e4f7e097999
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-object-creation"></a>动态对象创建
本文说明了如何在运行时动态地创建对象。 过程使用运行时类信息，如本文所述[访问运行时类信息](../mfc/accessing-run-time-class-information.md)。  
  
#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>在给定运行时类的情况下动态创建对象  
  
1.  使用以下代码，借助 `CreateObject` 的 `CRuntimeClass` 函数动态地创建一个对象。 请注意，在失败时，`CreateObject`返回**NULL**而不是引发异常：  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CObject](../mfc/using-cobject.md)

