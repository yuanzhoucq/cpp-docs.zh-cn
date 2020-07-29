---
title: 稳定性
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 9de2611e29f5f9bfd08839517e873c3dda225af0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211588"
---
# <a name="robustness"></a>稳定性

使用以下 C 运行时库函数以提高程序的可靠性。

## <a name="run-time-robustness-functions"></a>运行时可靠性函数

|函数|用途|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|如果运算符无法分配内存，则将控制权转移到错误处理机制 **`new`** 。|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|将 Win32 异常（C 结构的异常）处理为 C++ 类型的异常。|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安装要由 [terminate](../c-runtime-library/reference/terminate-crt.md) 调用的自身的终止函数。|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安装要由 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 调用的自身的终止函数。|

## <a name="see-also"></a>另请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
