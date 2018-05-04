---
title: 分配和释放内存为 BSTR |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- bstr
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46ab5ae9d6f0bfa98231cbc41aa4ae0d10b89537
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>为 BSTR 分配和释放内存
当你创建`BSTR`s 并将它们传递之间 COM 对象，你必须在将它们使用，以避免内存泄漏的内存一定要小心。 当`BSTR`保持接口中的，你必须释放其内存是完成。 但是，当`BSTR`通过接口外的，接收对象负责其内存管理。  
  
 分配和释放内存的规则一般情况下，为分配`BSTR`s 如下所示：  
  
-   当您调用到需要的函数`BSTR`自变量，你必须将分配的内存`BSTR`的调用之前和之后发布。 例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   当您调用返回的函数到`BSTR`，必须自己释放字符串。 例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   当实现返回的函数`BSTR`、 分配字符串，但不要释放它。 接收函数会释放内存。 例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)   
 [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx)   
 [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)

