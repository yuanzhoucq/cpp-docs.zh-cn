---
title: 通配符扩展
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 2d495f94f2e3fb7b88d235edc7b98f8e90775393
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209510"
---
# <a name="wildcard-expansion"></a>通配符扩展

## <a name="microsoft-specific"></a>Microsoft 专用

可以使用通配符（问号 (?) 和星号 (*)）在命令行上指定文件名和路径参数。

命令行参数将由调用的例程`_setargv`(或`_wsetargv`宽字符环境中)，默认情况下不会将通配符扩展到中的单独字符串`argv`字符串数组。 有关启用通配符扩展的详细信息，请参阅[展开通配符自变量](../c-language/expanding-wildcard-arguments.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[main：程序启动](../cpp/main-program-startup.md)