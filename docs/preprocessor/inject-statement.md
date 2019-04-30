---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383719"
---
# <a name="injectstatement"></a>inject_statement

**C++特定**

将其自变量作为源文本插入类型库标头。

## <a name="syntax"></a>语法

```
inject_statement("source_text")
```

### <a name="parameters"></a>参数

*source_text*<br/>
要插入类型库标头文件的源文本。

## <a name="remarks"></a>备注

该文本放置在用于将类型库内容包装在标头文件中的命名空间声明的开头。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)