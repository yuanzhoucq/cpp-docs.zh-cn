---
title: CDaoErrorInfo 结构
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304224"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 结构

`CDaoErrorInfo` 结构包含有关为数据访问对象（DAO）定义的错误对象的信息。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
struct CDaoErrorInfo
{
    long m_lErrorCode;
    CString m_strSource;
    CString m_strDescription;
    CString m_strHelpFile;
    long m_lHelpContext;
};
```

#### <a name="parameters"></a>参数

*m_lErrorCode*<br/>
数字 DAO 错误代码。 请参阅 DAO 帮助中的 "可捕获的数据访问错误" 主题。

*m_strSource*<br/>
最初生成错误的对象或应用程序的名称。 Source 属性指定一个字符串表达式，该表达式表示最初生成错误的对象;表达式通常是对象的类名。 有关详细信息，请参阅 DAO 帮助中的主题 "源属性"。

*m_strDescription*<br/>
与错误关联的描述性字符串。 有关详细信息，请参阅 DAO 帮助中的主题 "Description 属性"。

*m_strHelpFile*<br/>
Microsoft Windows 帮助文件的完全限定路径。 有关详细信息，请参阅 DAO 帮助中的主题 "HelpContext，帮助程序属性"。

*m_lHelpContext*<br/>
Microsoft Windows 帮助文件中的主题的上下文 ID。 有关详细信息，请参阅 DAO 帮助中的主题 "HelpContext，帮助程序属性"。

## <a name="remarks"></a>备注

MFC 不会将 DAO 错误对象封装在类中。 相反， [CDaoException](../../mfc/reference/cdaoexception-class.md)类提供一个接口用于访问 DAO `DBEngine` 对象中包含的错误集合，该对象还包含所有工作区。 当 MFC DAO 操作引发您捕获的 `CDaoException` 对象时，MFC 将填充 `CDaoErrorInfo` 结构并将其存储在异常对象的[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)成员中。 （如果选择直接调用 DAO，则必须自行调用 exception 对象的[GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成员函数来填充 `m_pErrorInfo`。）

有关处理 DAO 错误的详细信息，请参阅文章[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。 有关相关信息，请参阅 DAO 帮助中的主题 "Error Object"。

[CDaoException：： GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成员函数检索的信息存储在 `CDaoErrorInfo` 结构中。 检查在异常处理程序中捕获的 [ 对象中的 ](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)m_pErrorInfo`CDaoException` 数据成员， 或从显式创建的 `GetErrorInfo` 对象调用 `CDaoException` 以检查在直接调用过程中可能发生的错误到 DAO 接口。 `CDaoErrorInfo` 还在调试版本中定义了 `Dump` 成员函数。 您可以使用 `Dump` 转储 `CDaoErrorInfo` 对象的内容。

## <a name="requirements"></a>要求

**标头：** afxdao

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
