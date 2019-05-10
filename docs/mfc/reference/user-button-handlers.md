---
title: 用户按钮处理程序
ms.date: 11/04/2016
f1_keywords:
- ON_BN_HILITE
- ON_BN_DOUBLECLICKED
- ON_BN_CLICKED
- ON_BN_PAINT
- ON_BN_DISABLE
- ON_BN_UNHILITE
helpviewer_keywords:
- ON_BN_PAINT
- user buttons [MFC]
- ON_BN_DOUBLECLICKED [MFC]
- ON_BN_DISABLE [MFC]
- ON_BN_UNHILITE [MFC]
- ON_BN_HILITE [MFC]
- ON_BN_CLICKED [MFC]
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
ms.openlocfilehash: 1b79c781243b0af02479d37865a86577311789da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309728"
---
# <a name="user-button-handlers"></a>用户按钮处理程序

下面的映射条目对应于函数原型。

|映射条目|函数原型|
|---------------|------------------------|
|ON_BN_CLICKED( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_DISABLE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_DOUBLECLICKED( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_HILITE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_PAINT( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_UNHILITE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|

## <a name="see-also"></a>请参阅

[消息映射](../../mfc/reference/message-maps-mfc.md)
