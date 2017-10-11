---
title: "DHtmlUrlEventMapEntry 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 37e43514c116f93841b1479103a6f29ec708bfa0
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry 结构
`DHtmlUrlEventMapEntry`结构可提供多 URL 事件映射支持。  
  
## <a name="syntax"></a>语法  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>参数  
 `szUrl`  
 URL。  
  
 *pEventMap*  
 URL 与关联的事件映射。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdhtml.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


