---
title: "CUserException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [C++], stopping
- exceptions, throwing
- CUserException class
- errors [C++], trapping
- operations [C++]
- throwing exceptions, stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8548ffa7ad9032e174d650e210a70a29b0e3f19d
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cuserexception-class"></a>CUserException 类
引发后将终止最终用户操作。  
  
## <a name="syntax"></a>语法  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>备注  
 使用`CUserException`何时应使用 throw/catch 异常机制使用的特定于应用程序异常。 类名中的"用户"可以解释为"我的用户做一些我需要处理异常"。  
  
 一个`CUserException`在调用全局函数后，就会引发`AfxMessageBox`以通知用户的操作已失败。 当您编写异常处理程序时，专门因为用户通常已通知失败的处理异常。 在某些情况下，框架会引发此异常。 若要引发`CUserException`自己，向用户发出警报，然后调用全局函数`AfxThrowUserException`。  
  
 在下面的示例中，包含可能会失败的操作的函数会通知用户，并引发`CUserException`。 调用函数会捕获此异常，并专门对其进行处理︰  
  
 [!code-cpp[NVC_MFCExceptions #&24;](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 有关详细信息使用`CUserException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)

