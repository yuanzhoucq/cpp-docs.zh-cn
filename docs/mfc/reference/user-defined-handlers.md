---
title: 用户定义的处理程序
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.handlers
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: 4d2102668b7cc964e6fe3bffdcc6931a2961a737
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562248"
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

