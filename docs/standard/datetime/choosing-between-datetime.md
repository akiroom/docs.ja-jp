---
title: DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ed41d7739822d531986d65faa820ab7100c6651
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026563"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け

日時情報を使用する .NET アプリケーションは非常に多様であり、その情報をさまざまな方法で使用できます。 より一般的な日時情報の用途には、次の 1 つ以上が含まれます。

* 日付のみを反映する (時刻情報は重要ではない)。

* 時刻のみを反映する (日付情報は重要ではない)。

* 特定の時刻と場所に関連付けられていない抽象日時を反映する (たとえば、国際的チェーンのほとんどのストアは週中の午前 9:00 にオープンする)。

* .NET の外部ソースから日付と時刻の情報を取得するには、シンプルな日付と時刻の情報が格納される場所に通常のデータを入力します。

* 単一の時点を一意かつ明確に識別する。 ホスト システムでのみ日付と時刻を明確にする必要があるアプリケーションもあれば、システム全体で明確にする必要があるアプリケーションもあります (つまり、1 つのシステムでシリアル化される日付は有意に逆シリアル化し、世界中のどの場所においても別のシステムで使用できます)。

* 関連する複数の時刻を保持する (要求元の現地時刻やサーバーの Web 要求受信時刻など)。

* 日付と時刻の演算を実行する (これにより、おそらく単一時点が一意かつ明確に識別される)。

.NET が含まれています、 <xref:System.DateTime>、 <xref:System.DateTimeOffset>、 <xref:System.TimeSpan>、および<xref:System.TimeZoneInfo>型、すべての日付と時刻を使用するアプリケーションの構築に使用できます。

> [!NOTE]
> このトピックには 4 番目の型の <xref:System.TimeZone>については説明されません。その機能は、 <xref:System.TimeZoneInfo> クラスに完全に組み込まれているからです。 開発者は可能な限り、 <xref:System.TimeZoneInfo> クラスの代わりに <xref:System.TimeZone> クラスを使用する必要があります。

## <a name="the-datetime-structure"></a>DateTime 構造体

<xref:System.DateTime> 値は、特定の日付と時刻を定義します。 含まれています、<xref:System.DateTime.Kind%2A>プロパティを提供する制限については、タイム ゾーンその日付と時刻が属する。 <xref:System.DateTimeKind> プロパティによって返される <xref:System.DateTime.Kind%2A> 値は、 <xref:System.DateTime> 値が現地時刻 (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>)、世界協定時刻 (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>)、指定されていない時刻 (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>) のうちのどれを表すかを示します。

<xref:System.DateTime> 構造体は、次の操作を実行するアプリケーションに適しています。

* 日付のみを使用するアプリケーション。

* 時刻のみを使用するアプリケーション。

* 抽象日時を使用するアプリケーション。

* タイム ゾーン情報がない日時を使用するアプリケーション。

* UTC 日時のみを使用するアプリケーション。

* SQL データベースなどの .NET では、外部ソースから日付と時刻の情報を取得します。 通常、これらのソースは、 <xref:System.DateTime> 構造体と互換性のある単純な形式で日時情報を格納します。

* 日付と時刻の演算を実行しますが、これは一般的な結果に関するものです。 たとえば、6 カ月を特定の日付と時刻に加算する加算演算では、多くの場合、結果を夏時間に合わせて調整するかどうかは重要ではありません。

特定の <xref:System.DateTime> 値が UTC を表さない場合、通常、その日付と時刻の値は、あいまいであるか、その移植性に限定されます。 たとえば、 <xref:System.DateTime> 値が現地時刻を表す場合、そのローカル タイム ゾーン内で移植することができます (つまり、同じタイム ゾーンにある別のシステムで値が逆シリアル化されると、その値は明確に単一時点を識別します)。 ローカル タイム ゾーン外では、その <xref:System.DateTime> 値は複数の意味を持つ場合があります。 値の <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>の場合、移植性は低くなります。同じタイム ゾーン内であいまいになり、最初にシリアル化したのと同じシステムにおいてさえもあいまいになる可能性があります。 <xref:System.DateTime> 値が UTC を表す場合のみ、値が使用されるシステムまたはタイム ゾーンに関係なく、その値は明確に単一時点を識別します。

> [!IMPORTANT]
> <xref:System.DateTime> データを保存または共有する際、UTC を使用する必要があり、 <xref:System.DateTime> 値の <xref:System.DateTime.Kind%2A> プロパティを <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>に設定する必要があります。

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset 構造体

<xref:System.DateTimeOffset> 構造体は、日付と時刻の値、およびその値と UTC との差異を示すオフセットを表します。 そのため、値は常に明確に単一時点を識別します。

<xref:System.DateTimeOffset> 型には、 <xref:System.DateTime> 型のすべての機能に加え、タイム ゾーンの処理機能が含まれます。 これにより、次のようなアプリケーションには適しません。

* 単一の時点を一意かつ明確に識別する。 <xref:System.DateTimeOffset> 型を使用して、「現在」の意味を明確に定義し、トランザクションの時刻を記録し、システム イベントまたはアプリケーション イベントの時刻を記録し、ファイル作成時刻とファイル変更時刻を記録することができます。

* 一般的な日付と時刻の演算を実行する。

* その時刻が 2 つの別々の値または構造体の 2 つのメンバーである場合、関連する複数の時刻を保持する。

> [!NOTE]
> <xref:System.DateTimeOffset> 値のこの用途は、 <xref:System.DateTime> 値の用途と比べてはるかに一般的です。 その結果、 <xref:System.DateTimeOffset> はアプリケーション開発の既定の日付時刻型と見なされます。

<xref:System.DateTimeOffset> 値は特定のタイム ゾーンと関連付けられていませんが、さまざまなタイム ゾーンから派生することができます。 これを説明するために、いくつかの <xref:System.DateTimeOffset> 値 (ローカルの太平洋標準時を含む) が属することができるタイム ゾーンの一覧を次の例に示します。

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

この例の日付と時刻の値はそれぞれ少なくとも 3 つの異なるタイム ゾーンに属することができることを出力は示しています。 <xref:System.DateTimeOffset> 値の 6/10/2007 は、日付と時刻の値が夏時間を表す場合、UTC のそのオフセットは必ずしも元のタイム ゾーンの基本 UTC オフセット、またはその表示名から見つかる UTC のオフセットと一致しないことを示しています。 これは、単一の <xref:System.DateTimeOffset> 値はそのタイム ゾーンと密接に関連していないために夏時間との間のタイム ゾーンの遷移を反映することができないことを意味しています。 これは特に、日付と時刻の演算を使用して <xref:System.DateTimeOffset> 値を操作する際に問題となる可能性があります。 (タイム ゾーンの調整規則を考慮に入れた日付と時刻の演算を実行する方法については、「 [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)」をご覧ください)。

## <a name="the-timespan-structure"></a>TimeSpan 構造体

<xref:System.TimeSpan> 構造体は、時間間隔を表します。 その 2 つの一般的な用途は、次のとおりです。

* 2 つの日付と時刻の値の間の時間を反映する。 たとえば、ある値から <xref:System.DateTime> 値を減算すると、 <xref:System.TimeSpan> 値が返されます。

* 経過時間を測定する。 たとえば、<xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType>プロパティが返す、<xref:System.TimeSpan>値のいずれかへの呼び出しから経過した時間間隔を反映する、<xref:System.Diagnostics.Stopwatch>経過時間の測定を開始するメソッド。

値が特定時刻への参照がない値が時間を反映する際、 <xref:System.TimeSpan> 値の代わりに <xref:System.DateTime> 値を使用することもできます。 この使用法と似ています、<xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType>と<xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>返すプロパティを<xref:System.TimeSpan>日付への参照なしの時間を表す値です。 たとえば、 <xref:System.TimeSpan> 構造体を使用して、ストアの開店時刻または閉店時刻を反映したり、標準イベントが発生したときの時刻を表したりするために使用できます。

以下の例では、開店時刻と閉店時刻用の `StoreInfo` オブジェクト、およびストアのタイム ゾーンを表す <xref:System.TimeSpan> オブジェクトを含む <xref:System.TimeZoneInfo> 構造体を定義します。 構造体には、 `IsOpenNow` 、 `IsOpenAt`という 2 つのメソッドも含まれます。これは、ローカル タイム ゾーンにいると想定されるユーザーによって指定された時刻にストアがオープンするかどうかを示します。

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` 構造体をクライアント コードで次のように使用できます。

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo クラス

 <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone. <xref:System.TimeZoneInfo> クラスにより、日付と時刻を使用して、どの日付と時刻の値も明確に単一時点を識別できるようにすることができます。 <xref:System.TimeZoneInfo> クラスを拡張することもできます。 Windows システムで提供され、レジストリで定義されているタイム ゾーン情報に依存していますが、カスタムのタイム ゾーンの作成もサポートされています。 また、タイム ゾーン情報のシリアル化と逆シリアル化もサポートされています。

場合によっては、 <xref:System.TimeZoneInfo> クラスをフル活用するために、開発作業をさらに実行する必要が生じることもあります。 日付と時刻の値がタイム ゾーンを属していることがさらに作業を密結合しない場合は、必要があります。 アプリケーションが、日付と時刻とその関連タイム ゾーンをリンクするメカニズムを提供しない限り、そのタイム ゾーンから解除するには、特定の日付と時刻の値の簡単です。 この情報をリンクする 1 つの方法は、日付と時刻の値とその関連タイム ゾーン オブジェクトの両方を含むクラスまたは構造体を定義するという方法です。

日付と時刻のオブジェクトをインスタンスするときにその日付と時刻の値が属するタイム ゾーンがわかっている場合のみ、.NET でタイム ゾーンのサポートを利用できます。 特に Web またはネットワーク アプリケーションでは、これは該当しません。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
