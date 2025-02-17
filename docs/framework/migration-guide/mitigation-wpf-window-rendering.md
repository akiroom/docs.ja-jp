---
title: '軽減策: WPF ウィンドウのレンダリング'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf951ecb955a6597757387de1119267ebc58fdc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301449"
---
# <a name="mitigation-wpf-window-rendering"></a>軽減策: WPF ウィンドウのレンダリング

Windows 8 以上で実行している .NET Framework 4.6 では、マルチ モニターのシナリオで 1 つのディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。

## <a name="impact"></a>影響

一般に、複数のモニターで、クリッピングなしでウィンドウ全体を表示することが期待の動作です。 ただし、Windows 7 以前のバージョンでは、2 つ目のモニターにウィンドウの一部をレンダリングするとパフォーマンスに大きな影響があるため、WPF ウィンドウが 1 つのディスプレイの外部に拡張されるときにはクリッピングされます。

Windows 8 以上で複数のモニターに WPF ウィンドウをレンダリングする際の詳細な影響は、多数の要因に依存しているために、正確に数量化することはできません。 場合によっては、グラフィックを多用するアプリケーションを実行するユーザーや複数のモニターに及ぶウィンドウを使用するユーザーの場合は特に、依然としてパフォーマンスに望ましくない影響が生じることがあります。 または、.NET Framework の複数のバージョン間で一貫性のある動作が実現できれば十分な場合もあります 。

## <a name="mitigation"></a>軽減策

この変更を無効にして、WPF ウィンドウが 1 つのディスプレイを超える場合にクリッピングされるという、以前の動作に戻すこともできます。 これには、2 つの方法があります。

- `<EnableMultiMonitorDisplayClipping>` 要素をアプリケーションの構成ファイルの `<appSettings>` セクションに追加することにより、Windows 8 以降で実行中のアプリケーションでこの動作を無効にしたり有効にしたりすることができます。 たとえば、次の構成セクションにより、クリッピングなしのレンダリングが無効になります。

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>` 構成設定には、次の 2 つの値のいずれかを指定できます。

  - `true` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを有効にします。

  - `false` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを無効にします。

- これを行うには、アプリの起動時に <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> プロパティを `true` に設定します。

## <a name="see-also"></a>関連項目

- [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
