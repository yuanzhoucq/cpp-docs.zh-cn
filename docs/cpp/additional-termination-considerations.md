---
title: 附加终止注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: acbe2332-9d8a-4a58-a471-dd652a837384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54780b11e07819ca78eba89d9af5a8ba018cc9e4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401803"
---
# <a name="additional-termination-considerations"></a>附加终止注意事项
可以通过使用终止 c + + 程序`exit`，**返回**，或`abort`。 您可以使用 `atexit` 函数添加退出处理。 以下几节中讨论了这几个方面。  
  
## <a name="see-also"></a>请参阅  
 [启动和终止](../cpp/startup-and-termination-cpp.md)