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
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502926"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

包装 Windows API 函数，提供用于访问注册表的面向对象的接口。

## <a name="syntax"></a>语法

```
class CSettingsStore : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSettingsStore:: CSettingsStore](#csettingsstore)|构造 `CSettingsStore` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSettingsStore::Close](#close)|关闭打开的注册表项。|
|[CSettingsStore::CreateKey](#createkey)|打开指定的密钥, 如果不存在, 则创建它。|
|[CSettingsStore::DeleteKey](#deletekey)|删除指定的键及其所有子级。|
|[CSettingsStore::DeleteValue](#deletevalue)|删除 open 键的指定值。|
|[CSettingsStore::Open](#open)|打开指定的键。|
|[CSettingsStore::Read](#read)|检索指定密钥值的数据。|
|[CSettingsStore::Write](#write)|将一个值写入到注册表中的 open 键下。|

## <a name="remarks"></a>备注

成员函数`CreateKey`和`Open`非常类似。 如果注册表项已存在, `CreateKey` `Open`则以相同的方式运行。 但是, 如果该注册表项不存在, 则`CreateKey`将创建它, `Open`而将返回一个错误值。

## <a name="example"></a>示例

下面的示例演示如何使用`CSettingsStore`类的 Open 和 Read 方法。 此代码段是[工具提示演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>要求

**标头:** afxsettingsstore

##  <a name="close"></a>CSettingsStore:: Close

关闭打开的注册表项。

```
virtual void Close();
```

### <a name="remarks"></a>备注

默认情况下, 从[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)的析构函数中调用此方法。

##  <a name="createkey"></a>CSettingsStore:: CreateKey

打开注册表项, 如果不存在, 则创建它。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
中指定要创建或打开的项的名称。

### <a name="return-value"></a>返回值

如果成功, 则为 0;否则为非零值。

### <a name="remarks"></a>备注

`CreateKey`使用`m_hKey`作为注册表查询的根。 它搜索*pszPath*作为的子项`m_hKey`。 如果该键不存在, `CreateKey`则创建它。 否则, 会打开该密钥。 `CreateKey`然后, `m_hKey`将设置为创建或打开的键。

##  <a name="csettingsstore"></a>CSettingsStore:: CSettingsStore

创建一个 `CSettngsStore` 对象。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>参数

*bAdmin*<br/>
中指定`CSettingsStore`对象是否在管理员模式下操作的布尔参数。

*bReadOnly*<br/>
中指定是否`CSettingsStore`在只读模式下创建对象的布尔参数。

### <a name="remarks"></a>备注

如果将*bAdmin*设置为 TRUE, `m_hKey`则成员变量将设置为**HKEY_LOCAL_MACHINE**。 如果将*bAdmin*设置为 FALSE, `m_hKey`则将设置为**HKEY_CURRENT_USER**。

安全访问依赖于*bReadOnly*参数。 如果*bReadonly*为 FALSE, 则将安全访问权限设置为**KEY_ALL_ACCESS**。 如果*bReadyOnly*为 TRUE, 则安全访问将设置为**KEY_QUERY_VALUE、KEY_NOTIFY**和**KEY_ENUMERATE_SUB_KEYS**的组合。 有关安全访问和注册表的详细信息, 请参阅[注册表项安全和访问权限](/windows/win32/SysInfo/registry-key-security-and-access-rights)。

自动`CSettingsStore` 释放`m_hKey`的析构函数。

##  <a name="deletekey"></a>CSettingsStore::D eleteKey

从注册表中删除密钥及其所有子项。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
中要删除的键的名称。

*bAdmin*<br/>
中指定要删除的密钥位置的开关。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果`CSettingsStore`对象处于只读模式, 则此方法将失败。

如果参数*bAdmin*为零, `DeleteKey`则在**HKEY_CURRENT_USER**下搜索要删除的密钥。 如果*bAdmin*为非零`DeleteKey`值, 则会在**HKEY_LOCAL_MACHINE**下搜索要删除的密钥。

##  <a name="deletevalue"></a>CSettingsStore::D eleteValue

从中`m_hKey`删除值。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>参数

*pszValue*<br/>
中指定要删除的值字段。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="open"></a>CSettingsStore:: Open

打开注册表项。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
中注册表项的名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法成功打开指定的键后, 它会`m_hKey`将设置为此项的句柄。

##  <a name="read"></a>CSettingsStore:: Read

从注册表项中读取值。

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
中指向以 null 结尾的字符串的指针, 该字符串包含要从注册表中读取的值的名称。

*iVal*<br/>
弄对接收从注册表项中读取的值的整型变量的引用。

*dwVal*<br/>
弄对接收从注册表项中读取的值的32位双字变量的引用。

*sVal*<br/>
弄对接收从注册表项中读取的值的字符串变量的引用。

*scStringList*<br/>
弄对字符串列表变量的引用, 该变量接收从注册表项中读取的值。

*scArray*<br/>
弄对字符串数组变量的引用, 该变量接收从注册表项中读取的值。

*dwcArray*<br/>
弄对32位双字数组变量的引用, 该变量接收从注册表项中读取的值。

*wcArray*<br/>
弄对从注册表项中读取值的16位 word 数组变量的引用。

*bcArray*<br/>
弄对字节数组变量的引用, 该变量接收从注册表项中读取的值。

*lpPoint*<br/>
弄引用指向`POINT`结构的指针, 该结构接收从注册表项中读取的值。

*rect*<br/>
弄对[CRect](../../atl-mfc-shared/reference/crect-class.md)变量的引用, 该变量接收从注册表项中读取的值。

*ppData*<br/>
弄指向数据的指针的指针, 该数据接收从注册表项中读取的值。

*pBytes*<br/>
弄指向无符号整数变量的指针。 此变量接收*ppData*指向的缓冲区的大小。

*list*<br/>
弄对[CObList](../../mfc/reference/coblist-class.md)变量的引用, 该变量接收从注册表项中读取的值。

*obj*<br/>
弄对接收从注册表项中读取的值的[CObject](../../mfc/reference/cobject-class.md)变量的引用。

*pObj*<br/>
弄引用指向一个`CObject`变量的指针, 该变量接收从注册表项中读取的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Read`检查*pszKey*是否为的子项`m_hKey`。

##  <a name="write"></a>CSettingsStore:: Write

将一个值写入到注册表中的 open 键下。

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
中指向字符串的指针, 该字符串包含要设置的值的名称。

*iVal*<br/>
中对包含要存储的数据的整数变量的引用。

*dwVal*<br/>
中对包含要存储的数据的32位双字变量的引用。

*pszVal*<br/>
中一个指针, 指向以 null 结尾的字符串变量, 其中包含要存储的数据。

*scStringList*<br/>
中对包含要存储的数据的[CStringList](../../mfc/reference/cstringlist-class.md)变量的引用。

*bcArray*<br/>
中对包含要存储的数据的字节数组变量的引用。

*scArray*<br/>
中对包含要存储的数据的字符串数组变量的引用。

*dwcArray*<br/>
中对包含要存储的数据的32位双字数组变量的引用。

*wcArray*<br/>
中对包含要存储的数据的16位 word 数组变量的引用。

*rect*<br/>
中对包含要存储的数据的[CRect](../../atl-mfc-shared/reference/crect-class.md)变量的引用。

*lpPoint*<br/>
中引用指向包含要存储的`POINT`数据的变量的指针。

*pData*<br/>
中指向包含要存储的数据的缓冲区的指针。

*nBytes*<br/>
中指定*pData*参数指向的数据的大小 (以字节为单位)。

*list*<br/>
中对包含要存储的数据的[CObList](../../mfc/reference/coblist-class.md)变量的引用。

*obj*<br/>
中对包含要存储的数据的[CObject](../../mfc/reference/cobject-class.md)变量的引用。

*pObj*<br/>
中指向一个指针的指针, `CObject`该指针指向包含要存储的数据的变量。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

若要写入注册表, 在创建[CSettingsStore](../../mfc/reference/csettingsstore-class.md)对象时, 必须将*bReadOnly*设置为非零值。 有关详细信息, 请参阅[CSettingsStore:: CSettingsStore](#csettingsstore)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
