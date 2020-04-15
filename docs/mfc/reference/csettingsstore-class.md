---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318467"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

包装 Windows API 函数，提供用于访问注册表的面向对象的接口。

## <a name="syntax"></a>语法

```
class CSettingsStore : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSettingsStore：CSettingsStore](#csettingsstore)|构造 `CSettingsStore` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSettingsStore：关闭](#close)|关闭打开的注册表项。|
|[CSettingsStore：创建密钥](#createkey)|打开指定的密钥，如果不存在，则将其创建。|
|[CSettingsStore：:Delete密钥](#deletekey)|删除指定的密钥及其所有子级。|
|[CSettingsStore：:Delete值](#deletevalue)|删除打开密钥的指定值。|
|[CSettingsStore：：打开](#open)|打开指定的密钥。|
|[设置存储：阅读](#read)|检索指定键值的数据。|
|[CSettingsStore：写入](#write)|在打开的键下向注册表写入值。|

## <a name="remarks"></a>备注

成员的功能`CreateKey`和`Open`非常相似。 如果注册表项已存在，`CreateKey`并且`Open`以相同的方式运行。 但是，如果注册表项不存在，`CreateKey`将创建它，而`Open`将返回错误值。

## <a name="example"></a>示例

下面的示例演示如何使用`CSettingsStore`类的"打开"和"读取"方法。 此代码段是[工具提示演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>要求

**标题：** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore：关闭

关闭打开的注册表项。

```
virtual void Close();
```

### <a name="remarks"></a>备注

默认情况下，此方法是从[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)的析构函数调用的。

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore：创建密钥

打开注册表项或创建注册表项（如果不存在）。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[在]指定要创建或打开的键的名称。

### <a name="return-value"></a>返回值

0 如果成功;否则为非零值。

### <a name="remarks"></a>备注

`CreateKey`用作`m_hKey`注册表查询的根。 它搜索*pszPath*作为 的`m_hKey`子键。 如果密钥不存在，`CreateKey`请创建它。 否则，它将打开密钥。 `CreateKey`然后设置`m_hKey`到创建或打开的键。

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore：CSettingsStore

创建一个 `CSettngsStore` 对象。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>参数

*bAdmin*<br/>
[在]布尔参数，用于指定`CSettingsStore`对象是否在管理员模式下运行。

*b 只读*<br/>
[在]布尔参数，用于指定对象是否`CSettingsStore`以只读模式创建。

### <a name="remarks"></a>备注

如果*bAdmin*设置为 TRUE，`m_hKey`则成员变量设置为**HKEY_LOCAL_MACHINE**。 如果将*bAdmin*设置为 FALSE，`m_hKey`则设置为**HKEY_CURRENT_USER**。

安全访问取决于*bReadOnly*参数。 如果*bReadONLY*为 FALSE，则安全访问将设置为**KEY_ALL_ACCESS**。 如果*bReadyOnly*为 TRUE，则安全访问将设置为**KEY_QUERY_VALUE、KEY_NOTIFY**和**KEY_ENUMERATE_SUB_KEYS**的组合。 有关安全访问与注册表的详细信息，请参阅[注册表密钥安全和访问权限](/windows/win32/SysInfo/registry-key-security-and-access-rights)。

自动释放`CSettingsStore``m_hKey`的析构函数。

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore：:Delete密钥

从注册表中删除密钥及其所有子级。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[在]要删除的键的名称。

*bAdmin*<br/>
[在]指定要删除的键的位置的交换机。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果对象处于只读模式`CSettingsStore`，此方法将失败。

如果参数*bAdmin*为零`DeleteKey`，则搜索**要删除的键HKEY_CURRENT_USER**。 如果*bAdmin*是非零`DeleteKey`，则搜索要删除**的HKEY_LOCAL_MACHINE**下的密钥。

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore：:Delete值

从`m_hKey`中删除 值。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>参数

*pszValue*<br/>
[在]指定要删除的值字段。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore：：打开

打开注册表项。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[在]注册表项的名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法成功打开指定的密钥后，它将设置`m_hKey`为此密钥的句柄。

## <a name="csettingsstoreread"></a><a name="read"></a>设置存储：阅读

从注册表中的键读取值。

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>参数

*pszKey*<br/>
[在]指向 null 终止字符串的指针，该字符串包含要从注册表读取的值的名称。

*伊瓦尔*<br/>
[出]引用从注册表键读取的值的整数变量。

*德瓦尔*<br/>
[出]引用从注册表键读取的值的 32 位双字变量。

*斯瓦尔*<br/>
[出]引用从注册表键读取的值的字符串变量。

*scStringlist*<br/>
[出]引用从注册表键读取的值的字符串列表变量。

*scArray*<br/>
[出]引用从注册表键读取的值的字符串数组变量。

*dwcArray*<br/>
[出]引用 32 位双字数组变量，该变量接收从注册表项读取的值。

*wcArray*<br/>
[出]引用从注册表键读取的值的 16 位单词数组变量。

*bcArray*<br/>
[出]引用从注册表键读取的值的字节数组变量。

*lpPoint*<br/>
[出]引用指向从注册表键读取`POINT`的值的结构的指针。

*矩形*<br/>
[出]引用从注册表项读取的值的[CRect](../../atl-mfc-shared/reference/crect-class.md)变量。

*ppData*<br/>
[出]指向从注册表键读取的值的数据的指针。

*p字节*<br/>
[出]指向无符号整数变量的指针。 此变量接收*ppData*指向的缓冲区的大小。

*list*<br/>
[出]引用从注册表项读取的值的[CObList](../../mfc/reference/coblist-class.md)变量。

obj**<br/>
[出]引用从注册表键读取的值的[CObject](../../mfc/reference/cobject-class.md)变量。

*pObj*<br/>
[出]引用指向从注册表键读取`CObject`的值的变量的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Read`检查*pszKey*作为 的`m_hKey`子键。

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore：写入

在打开的键下向注册表写入值。

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>参数

*pszKey*<br/>
[在]指向包含要设置的值名称的字符串的指针。

*伊瓦尔*<br/>
[在]对包含要存储的数据的整数变量的引用。

*德瓦尔*<br/>
[在]引用包含要存储的数据的 32 位双字变量。

*pszVal*<br/>
[在]指向包含要存储数据的 null 终止字符串变量的指针。

*scStringlist*<br/>
[在]引用包含要存储的数据的[CStringList](../../mfc/reference/cstringlist-class.md)变量。

*bcArray*<br/>
[在]对包含要存储的数据的字节数组变量的引用。

*scArray*<br/>
[在]对包含要存储数据的字符串数组变量的引用。

*dwcArray*<br/>
[在]引用包含要存储的数据的 32 位双字数组变量。

*wcArray*<br/>
[在]引用包含要存储的数据的 16 位单词数组变量。

*矩形*<br/>
[在]对包含要存储的数据的[CRect](../../atl-mfc-shared/reference/crect-class.md)变量的引用。

*lpPoint*<br/>
[在]引用指向包含要存储的数据`POINT`的变量的指针。

*pData*<br/>
[在]指向包含要存储的数据的缓冲区的指针。

*n 字节*<br/>
[在]指定*pData*参数指向的数据的大小（以字节为单位）。

*list*<br/>
[在]引用包含要存储的数据的[CObList](../../mfc/reference/coblist-class.md)变量。

obj**<br/>
[在]对包含要存储数据的[CObject](../../mfc/reference/cobject-class.md)变量的引用。

*pObj*<br/>
[在]指向包含要存储的数据的`CObject`变量的指针。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

为了写入注册表，在创建[CSettingsStore](../../mfc/reference/csettingsstore-class.md)对象时，必须将*bReadOnly*设置为非零值。 有关详细信息，请参阅[CSettingsStore：CSettingsStore](#csettingsstore)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
