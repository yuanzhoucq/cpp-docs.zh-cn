---
title: 编译器 COM 全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034124"
---
# <a name="compiler-com-global-functions"></a>编译器 COM 全局函数

**Microsoft 专用**

下列例程可用：

|函数|描述|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|将引发[_com_error](../cpp/com-error-class.md)中响应失败。|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|替换用于 COM 错误处理的默认函数。|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|将转换`BSTR`值设为`char *`。|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|将转换`char *`值设为`BSTR`。|

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)<br/>
[编译器 COM 支持](../cpp/compiler-com-support.md)