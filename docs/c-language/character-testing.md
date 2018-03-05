---
title: "字符测试 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeea6573b49e3bb093c3eb343ac3c89c27f0466b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="character-testing"></a>字符测试
**ANSI 4.3.1**：由 `isalnum`、`isalpha`、`iscntrl`、`islower`、`isprint` 和 `isupper` 函数测试的字符集  
  
 以下列表描述了由 Microsoft C 编译器实现的这些函数。  
  
|函数|测试|  
|--------------|---------------|  
|`isalnum`|字符 0 - 9、A-Z、a–z ASCII 48-57、65-90、97-122|  
|`isalpha`|字符 A-Z、a–z ASCII 65-90、97-122|  
|`iscntrl`|ASCII 0 -31、127|  
|`islower`|字符 a-z ASCII 97-122|  
|`isprint`|字符 A–Z、a–z、0 - 9、标点、空格 ASCII 32–126|  
|`isupper`|字符 A-Z ASCII 65-90|  
  
## <a name="see-also"></a>请参阅  
 [库函数](../c-language/library-functions.md)