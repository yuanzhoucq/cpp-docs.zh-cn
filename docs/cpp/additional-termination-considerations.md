---
title: 附加终止注意事项 |Microsoft 文档
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
ms.openlocfilehash: b634c7c792d4462f96f022f223d0b1eec2a750ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="additional-termination-considerations"></a>附加终止注意事项
你可以通过使用终止 C++ 程序**退出**， `return`，或**中止**。 您可以使用 `atexit` 函数添加退出处理。 以下几节中讨论了这几个方面。  
  
## <a name="see-also"></a>请参阅  
 [启动和终止](../cpp/startup-and-termination-cpp.md)