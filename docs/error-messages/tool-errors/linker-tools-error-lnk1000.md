---
title: 链接器工具错误 LNK1000 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f67df9c53b79fabfc9559380b5b57a72e64cb8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1000"></a>链接器工具错误 LNK1000
未知的错误;请查阅文档以技术支持选项  
  
 注意错误的情况，可尝试隔离问题并创建可重现的测试用例，然后联系`Microsoft Product Support Services`。 有关如何调查并报告这些错误的信息，请参阅[ http://support.microsoft.com/default.aspx?scid=kb; en-我们; 134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650)。  
  
 如果混合使用标准头文件 (例如，dos.h) 和你自己的文件，则可能出现此错误。 `#include` 标准标头首先后, 跟你自己的标头文件。