---
title: 通配符扩展 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82bb280036bf8ad1886d2943c3ec3e546c2eaff2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466171"
---
# <a name="wildcard-expansion"></a>通配符扩展
## <a name="microsoft-specific"></a>Microsoft 专用  
 可以使用通配符（问号 (?) 和星号 (*)）在命令行上指定文件名和路径参数。  
  
 命令行参数将由调用的例程`_setargv`(或`_wsetargv`宽字符环境中)，默认情况下不会将通配符扩展到中的单独字符串`argv`字符串数组。 有关启用通配符扩展的详细信息，请参阅[展开通配符自变量](../c-language/expanding-wildcard-arguments.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)