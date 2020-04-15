---
title: TN059：使用MFC MBCS-Unicode转换宏
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 0d63a87d0fddde30dd5cbb18207297a345d74b9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366581"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059：使用 MFC MBCS/Unicode 转换宏

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明描述如何将 AFXPRIV.H 中定义的宏用于 MBCS/Unicode 转换。 如果您的应用程序直接处理 OLE API，或出于某种原因经常需要在 Unicode 和 MBCS 之间进行转换，则这些宏会最有用。

## <a name="overview"></a>概述

在 MFC 3.x 中，调用 OLE 接口时已使用特殊的 DLL (MFCANS32.DLL) 在 Unicode 和 MBCS 之间自动转换。 此 DLL 是一个几乎透明的层，它允许编写 OLE 应用程序，就像 OLE API 和接口是 MBCS 一样，即使它们始终是 Unicode（在 Macintosh 上除外）。 尽管该层非常方便，并且能够将应用程序快速地从 Win16 移植到 Win32（MFC、Microsoft Word、Microsoft Excel 和 VBA，它们只是使用该技术的 Microsoft 应用程序中的一部分），但它有时会对性能产生显著影响。 由于这个原因，MFC 4.x 不使用此 DLL，而是直接与 Unicode OLE 接口进行通信。 为此，MFC 在调用 OLE 接口时需要将 Unicode 转换为 MBCS，并且在实现 OLE 接口时通常需要从 Unicode 转换为 MBCS。 若要高效轻松地处理此问题，可创建大量宏以使该转换更简单。

创建这样一组宏的一个最大障碍是内存分配。 由于无法就地转换字符串，因此必须分配用于保存转换结果的新内存。 可以使用类似于以下内容的代码完成此操作：

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

此方法存在许多问题。 主要问题是要编写、测试和调试大量代码。 过去的简单函数调用现在变得更为复杂。 此外，执行此操作会产生大量运行时开销。 必须在堆上分配内存，并且每当完成转换后释放内存。 最后，以上代码将需要为 Unicode 和 Macintosh 版本（不需要进行此转换）添加适当的 `#ifdefs`。

我们已提出的解决方案是创建一些宏，这些宏将 1) 掩盖各种平台之间的差异；2) 使用高效的内存分配方案；3) 易于插入到现有源代码中。 以下是某个定义的示例：

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

使用此宏而不是上述代码，并且操作更为简单：

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

有一些需要转换的额外调用，但可轻松而高效地使用宏。

每个宏的实现都使用 _alloca() 函数从堆栈而非堆中分配内存。 从堆栈中分配内存要比在堆上分配内存快得多，并且在退出该函数时，将自动释放内存。 此外，宏避免调用`MultiByteToWideChar`（或`WideCharToMultiByte`） 多个次。 这可通过分配比所需内存量多一点的内存来实现。 我们知道，MBC 将最多转换为一个**WCHAR，** 并且对于每个**WCHAR，** 我们最多将有两个 MBC 字节。 通过分配比所需内存多一点但始终足以处理转换的内存，避免对转换函数进行第二次调用。 对帮助器函数`AfxA2Whelper`的调用减少了为执行转换而必须执行的参数推送数（这会导致代码更小，而不是直接调用）。 `MultiByteToWideChar`

若要使宏拥有存储临时长度的空间，需要声明称为 _convert 的局部变量，该变量在使用转换宏的每个函数中都执行此操作。 这将通过调用 USES_CONVERSION 宏实现，如示例的上述内容所示。

同时存在泛型转换宏和 OLE 特定的宏。 下面讨论了这两个不同的宏设置。 所有宏位于 AFXPRIV.H 中。

## <a name="generic-conversion-macros"></a>泛型转换宏

泛型转换宏形成了基础机制。 上一部分 (A2W) 中显示的宏示例和实现是此类“泛型”宏之一。 它不与 OLE 特别相关。 下面列出了泛型宏的组：

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

除了执行文本转换外，还有用于转换 `TEXTMETRIC`、`DEVMODE`、`BSTR` 和 OLE 分配的字符串的宏和 Helper 函数。 这些宏超出了本讨论的范围 - 请参阅 AFXPRIV。H 了解有关这些宏的详细信息。

## <a name="ole-conversion-macros"></a>OLE 转换宏

OLE 转换宏专为处理预期**OLESTR**字符的功能而设计。 如果检查 OLE 标头，您将看到许多对**LPCOLESTR**和**OLECHAR**的引用。 这些类型用于以一种非特定于平台的方法引用 OLE 接口中使用的字符类型。 **OLECHAR**映射到 Win16 和 Macintosh 平台中的**字符**，在 Win32 中映射到**WCHAR。**

为了将 MFC 代码中 **#ifdef**指令的数量降至最低，对于涉及 OLE 字符串的每个转换，我们都有类似的宏。 下列宏是最常使用的：

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

同样，对于执行 TEXTMETRIC、DEVMODE、BSTR 和 OLE 分配的字符串，也有类似的宏。 有关更多信息，请参考 AFXPRIV.H。

## <a name="other-considerations"></a>其他注意事项

请勿在紧凑循环中使用宏。 例如，你不想编写以下类型的代码：

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

上述代码可能导致在堆栈上分配内存（以 MB 为单位），取决于字符串 `lpsz` 的内容！ 它还花时间转换循环的每个迭代的字符串。 相反，请将此类常量转换移出循环：

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

如果字符串不是常量，则将方法调用封装到函数中。 这将允许每次都释放转换缓冲区。 例如：

```
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

绝不返回某个宏的结果，除非返回值表示会在返回前创建数据副本。 例如，此代码是错误的：

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

可以通过将返回值更改为复制值的内容来修复上述代码：

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

虽然宏易于使用和插入到代码中，但从上面的警告可看出，你在使用宏时要特别谨慎。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
