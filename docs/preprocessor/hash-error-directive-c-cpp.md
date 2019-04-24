---
title: '#错误指令 (C /C++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037839"
---
# <a name="error-directive-cc"></a>#error 指令 (C/C++)
**#Error**指令在编译时发出用户指定的错误消息，然后终止编译。

## <a name="syntax"></a>语法

```
#errortoken-string
```

## <a name="remarks"></a>备注

此指令发出的错误消息包括*令牌字符串*参数。 *令牌字符串*参数不受宏扩展。 此指令通知程序不一致的开发人员或违反约束在预处理过程会十分有用。 下面的示例演示如何处理在预处理期间出错：

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)