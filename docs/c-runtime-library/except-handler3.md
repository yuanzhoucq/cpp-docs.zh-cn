---
title: _except_handler3
ms.date: 11/04/2016
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 0dfe007d7b444401accbf547674f96f7f7d54ac1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741312"
---
# <a name="excepthandler3"></a>_except_handler3

内部 CRT 函数。 由框架用于查找相应的异常处理程序，以处理当前异常。

## <a name="syntax"></a>语法

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>参数

*exception_record*<br/>
[in] 有关特定异常的信息。

*registration*<br/>
[in] 指示应该使用哪一个范围表查找异常处理程序的记录。

*context*<br/>
[in] 保留。

*dispatcher*<br/>
[in] 保留。

## <a name="return-value"></a>返回值

如果应该消除某个异常，则返回 `DISPOSITION_DISMISS`。 如果应该将异常向上传递一个等级给封装的异常处理程序，则返回 `DISPOSITION_CONTINUE_SEARCH`。

## <a name="remarks"></a>备注

如果此方法找到了相应的异常处理程序，则它会将异常传递给该处理程序。 在这种情况下，此方法不会返回到调用它的代码且与返回值无关。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
