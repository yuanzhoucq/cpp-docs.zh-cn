---
title: CString 语义 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1765f1f7f4103b1b2cfe6012b42ebef12f8863f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-semantics"></a>CString 语义
即使[CString](../atl-mfc-shared/reference/cstringt-class.md)对象可以增长的动态对象，它们充当内置的基元类型和简单的类。 每个`CString`对象表示一个唯一值。 `CString` 对象应认为是实际的字符串，而不是指向字符串的指针。  
  
 你可以指定一个**CString**到另一个对象。 但是，当你修改两种状态之一`CString`对象时，其他`CString`未修改对象，如下面的示例所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 请注意，在该示例，这两个`CString`对象被视为"等于"，因为它们表示相同的字符字符串。 `CString`类重载相等运算符 (`==`) 来比较两个`CString`对象基于其值 （内容） 而不是其标识 （地址）。  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

