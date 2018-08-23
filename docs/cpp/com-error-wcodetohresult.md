---
title: _com_error::WCodeToHRESULT |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f777b1de83b19727bca5e1b498c5380604f6688
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404536"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Microsoft 专用**  
  
 映射 16 位*wCode*为 32 位 HRESULT。  
  
## <a name="syntax"></a>语法  
  
```    
static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 *WCode*  
 16 位*wCode*要映射到 32 位的 HRESULT。  
  
## <a name="return-value"></a>返回值  
 映射从 16 位的 32 位 HRESULT *wCode*。  
  
## <a name="remarks"></a>备注  
 请参阅[WCode](../cpp/com-error-wcode.md)成员函数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error 类](../cpp/com-error-class.md)