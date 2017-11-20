---
title: "_com_error::HRESULTToWCode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::HRESULTToWCode
dev_langs: C++
helpviewer_keywords: HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2dac335f3cc2ea26602a5f8a91a47db7d1ebe39b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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