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
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857172"
---
# <a name="wildcard-expansion"></a>通配符扩展

**Microsoft 专用**

可以使用通配符（问号 (?) 和星号 (*)）在命令行上指定文件名和路径参数。

命令行参数由称为 `_setargv` 的例程（或宽字符环境中 `_wsetargv`）处理，默认情况下，它不会将通配符扩展到 `argv` 字符串数组中的单独字符串中。 有关启用通配符扩展的详细信息，请参阅[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[main：程序启动](../cpp/main-program-startup.md)