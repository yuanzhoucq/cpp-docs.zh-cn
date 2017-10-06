---
title: "通配符扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
caps.latest.revision: 9
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 779a788cae6523a48a82694e55edf3c1da5519d7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="wildcard-expansion"></a>通配符扩展
## <a name="microsoft-specific"></a>Microsoft 专用  
 可以使用通配符（问号 (?) 和星号 (*)）在命令行上指定文件名和路径参数。  
  
 命令行自变量由调用的例程**_setargv** (或**_wsetargv**宽字符环境中)，后者的默认设置不将通配符展开到单独字符串中`argv`字符串数组。 有关启用通配符扩展的详细信息，请参阅[展开通配符自变量](../c-language/expanding-wildcard-arguments.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [main：程序启动](../cpp/main-program-startup.md)
