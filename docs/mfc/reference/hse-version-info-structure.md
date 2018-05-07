---
title: HSE_VERSION_INFO 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acdf63e062aab1407daee461e22f00f5d3c59cee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 结构
由 `pVer` 成员函数中的 `CHttpServer::GetExtensionVersion` 参数指向此结构。 它提供 ISA 的 ISA 版本号和文本说明。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>参数  
 *dwExtensionVersion*  
 ISA 版本号  
  
 *lpszExtensionDesc*  
 ISA 的文本说明。 默认实现提供占位符文本；重写 `CHttpServer::GetExtensionVersion` 可提供您自己的说明。  
  
## <a name="requirements"></a>要求  
 **标头：** httpext.h  
  
## <a name="see-also"></a>请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

