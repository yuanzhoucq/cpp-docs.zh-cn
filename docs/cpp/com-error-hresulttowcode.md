---
title: "_com_error::HRESULTToWCode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HRESULTToWCode
- _com_error.HRESULTToWCode
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 296c6f43c1bc840ae13bdf4ad355d7f41e2cc3fd
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Microsoft 专用**  
  
 映射 32 位`HRESULT`到 16 位`wCode`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `hr`  
 32 位`HRESULT`映射到 16 位`wCode`。  
  
## <a name="return-value"></a>返回值  
 16 位`wCode`从 32 位映射`HRESULT`。  
  
## <a name="remarks"></a>备注  
 请参阅[_com_error:: wcode](../cpp/com-error-wcode.md)有关详细信息。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error 类](../cpp/com-error-class.md)
