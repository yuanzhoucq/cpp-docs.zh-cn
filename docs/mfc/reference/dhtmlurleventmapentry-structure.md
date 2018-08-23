---
title: DHtmlUrlEventMapEntry 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee629d9dcffc80ce20306989cad72d466722af87
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123326"
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
 *szUrl*  
 URL。  
  
 *pEventMap*  
 URL 与关联的事件映射。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdhtml.h  
  
## <a name="see-also"></a>请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

