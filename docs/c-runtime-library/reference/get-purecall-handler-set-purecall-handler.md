---
title: _get_purecall_handler、_set_purecall_handler
ms.date: 11/04/2016
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 0009b4bc1c7bf70bd84b9a82ecdc8643789e8164
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646351"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler、_set_purecall_handler

获取或设置纯虚函数调用的错误处理程序。

## <a name="syntax"></a>语法

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>参数

*函数*<br/>
要在调用纯虚函数时调用的函数。 一个 **_purecall_handler 中**函数必须具有 void 返回类型。

## <a name="return-value"></a>返回值

以前 **_purecall_handler 中**。 返回**nullptr**如果没有任何先前处理程序。

## <a name="remarks"></a>备注

**_Get_purecall_handler**并 **_set_purecall_handler**函数是特定于 Microsoft 的和仅适用于 c + + 代码。

对纯虚拟函数的调用出错，因为它没有实现。 默认情况下，在调用纯虚函数时，编译器将生成代码来调用错误处理程序函数，这将终止该程序。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 若要使用错误处理程序，创建具有的函数 **_purecall_handler 中**签名，然后使用 **_set_purecall_handler**使它成为当前处理程序。

因为只有一个 **_purecall_handler 中**每个进程，在调用时 **_set_purecall_handler**立即会影响所有线程。 任一线程上的最后一个调用方将设置该处理程序。

若要还原默认行为，请调用 **_set_purecall_handler**通过使用**nullptr**参数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_purecall_handler**， **_set_purecall_handler**|\<cstdlib> 或 \<stdlib.h>|

有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
