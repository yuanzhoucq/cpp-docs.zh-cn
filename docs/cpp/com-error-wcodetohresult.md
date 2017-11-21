---
title: "_com_error::WCodeToHRESULT |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::WCodeToHRESULT
dev_langs: C++
helpviewer_keywords: WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 925e1f7a2675dc0aaed3a0cab064e01681de673c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Microsoft 专用**  
  
 将 16 位 `wCode` 映射到 32 位 `HRESULT`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `wCode`  
 要映射为 32 位 `wCode` 的 16 位 `HRESULT`。  
  
## <a name="return-value"></a>返回值  
 已从 16 位 `HRESULT` 映射的 32 位 `wCode`。  
  
## <a name="remarks"></a>备注  
 请参阅[WCode](../cpp/com-error-wcode.md)成员函数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error 类](../cpp/com-error-class.md)