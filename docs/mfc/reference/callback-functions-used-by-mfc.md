---
title: "MFC 使用的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions, MFC
- MFC, callback functions
- functions [C++], callback
- callback functions
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b4d104fa76347da43c84611672f843511f0f3725
ms.lasthandoff: 02/24/2017

---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数
在 Microsoft 基础类库中显示三个回调函数。 传递给回调函数的说明[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，和[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)遵循本主题。 回调函数的常规用法，请参阅备注部分中的这些成员函数。 请注意所有的回调函数必须捕获返回到 Windows 帐户，因为不能跨回调边界引发异常之前的 MFC 异常。 关于异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


