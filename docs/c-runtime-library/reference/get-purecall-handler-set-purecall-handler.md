---
title: _get_purecall_handler、_set_purecall_handler
ms.date: 11/04/2016
api_name:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 73fc2ffe5cd4ed65c8695432b53816090bbc5f8e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955678"
---
# <a name="_get_purecall_handler-_set_purecall_handler"></a>_get_purecall_handler、_set_purecall_handler

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
要在调用纯虚函数时调用的函数。 **_Purecall_handler**函数必须具有 void 返回类型。

## <a name="return-value"></a>返回值

上一个 **_purecall_handler**。 如果没有上一个处理程序，则返回**nullptr** 。

## <a name="remarks"></a>备注

**_Get_purecall_handler**和 **_Set_purecall_handler**函数是 Microsoft 特定的，仅适用于C++代码。

对纯虚拟函数的调用出错，因为它没有实现。 默认情况下，在调用纯虚函数时，编译器将生成代码来调用错误处理程序函数，这将终止该程序。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 若要使用自己的错误处理程序，请创建具有 **_purecall_handler**签名的函数，然后使用 **_set_purecall_handler**使其成为当前处理程序。

由于每个进程只有一个 **_purecall_handler** ，因此当调用 **_set_purecall_handler**时，它会立即影响所有线程。 任一线程上的最后一个调用方将设置该处理程序。

若要还原默认行为，请使用**nullptr**参数调用 **_set_purecall_handler** 。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_purecall_handler**、 **_set_purecall_handler**|\<cstdlib> 或 \<stdlib.h>|

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
