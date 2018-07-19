---
title: CString 语义 |Microsoft Docs
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
ms.openlocfilehash: b1638b279f0bd9ee968451ea75ec1c5549e369d9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886149"
---
# <a name="cstring-semantics"></a>CString 语义
即使[CString](../atl-mfc-shared/reference/cstringt-class.md)对象可以增长的动态对象，它们充当内置基元类型和简单的类。 每个`CString`对象表示一个唯一值。 `CString` 对象应认为是为实际字符串而不是指向字符串的指针。  
  
 可以指定一个`CString`到另一个对象。 但是，如果修改两个`CString`对象，其他`CString`未修改对象，如以下示例所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 请注意，在该示例的两个`CString`对象被视为"equal"，因为它们表示相同的字符字符串。 `CString`类会重载相等运算符 (`==`) 来比较两个`CString`对象基于其值 （内容） 而不是其标识 （地址）。  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

