---
title: 用户定义的处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50348d36badb955a14f15e30d846b052b297b4a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442534"
---
# <a name="user-defined-handlers"></a>用户定义的处理程序

下面的映射条目对应于函数原型。

|映射条目|函数原型|
|---------------|------------------------|
|ON_MESSAGE (\<消息 >， \<memberFxn >)|afx_msg LRESULT memberFxn （WPARAM，LPARAM）;|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >， \<memberFxn >)|afx_msg LRESULT memberFxn （WPARAM，LPARAM）;|
|ON_THREAD_MESSAGE (\<消息 >， \<memberFxn >)|afx_msg void memberFxn （WPARAM，LPARAM）;|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >， \<memberFxn >)|afx_msg void memberFxn （WPARAM，LPARAM）;|

## <a name="see-also"></a>请参阅

[消息映射](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)

