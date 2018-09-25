---
title: DHtmlUrlEventMapEntry 结构 |Microsoft Docs
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
ms.openlocfilehash: bbac4b372f06f288eede8c578372d45334a5d707
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427519"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry 结构

`DHtmlUrlEventMapEntry`结构提供了多 URL 事件映射支持。

## <a name="syntax"></a>语法

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>参数

*szUrl*<br/>
URL。

*pEventMap*<br/>
使用 URL 相关联的事件映射。

## <a name="requirements"></a>要求

**标头：** afxdhtml.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

