---
title: 调用约定、参数和返回类型
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 15631b305246cbfd7dcd8081cb1ee488bf225fec
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264798"
---
# <a name="calling-conventions-parameters-and-return-type"></a>调用约定、参数和返回类型

Helper 例程的原型是：

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>参数

*pidd*<br/>
一个`const`指针，指向`ImgDelayDescr`，其中包含各种与导入相关的数据、 绑定信息时的时间戳和一组提供有关描述符内容的详细信息的属性的偏移量。 目前只有一个特性， `dlattrRva`，这表示描述符中的地址是相对虚拟地址。 有关详细信息，请参阅中的声明*delayimp.h*。

定义`PCImgDelayDescr`结构，请参阅[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)。

*ppfnIATEntry*<br/>
指向延迟加载导入地址表 (IAT) 导入的函数的地址使用更新中的槽的指针。 帮助器例程需要存储它返回到此位置的相同值。

## <a name="expected-return-values"></a>预期的返回值

如果函数运行成功，则返回导入函数的地址。

如果函数运行失败，将引发异常，并且返回 0。 引发的异常有三种类型：

- 无效参数，发生在 `pidd` 中的特性未正确指定时。

- `LoadLibrary` 在指定的 DLL 上失败。

- 
  `GetProcAddress` 失败。

它由你负责处理这些异常。

## <a name="remarks"></a>备注

Helper 函数的调用约定是 `__stdcall`。 返回值的类型无关，所以使用 FARPROC。 该函数具有 C 链接。

除非要将 Helper 例程用作通知挂钩，否则延迟加载 Helper 的返回值需要存储在已传入函数指针的位置。 在这种情况下，由你的代码负责查找要返回的适当函数指针。 然后，链接器生成的 thunk 代码可将该返回值用作导入的实际目标并直接跳转到该目标。

## <a name="sample"></a>示例

以下代码显示如何实现一个简单的挂钩函数。

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>请参阅

[了解 Helper 函数](../../build/reference/understanding-the-helper-function.md)