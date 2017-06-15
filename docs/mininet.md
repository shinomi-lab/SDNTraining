## Mininetの使い方

### 起動方法

2種類の方法がある。
基本的にはファイルから作成する方法を使うことになると思う。

```sh
# コマンドで作成
sudo mn --mac --switch=ovsk,protocols=OpenFlow13 --controller=remote,ip=127.0.0.1,port=6653
# ファイルから作成
sudo python create_simple_network.py
```

上記の```create_simple_network.py```は例えばこんな感じ。

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

from mininet.topo import Topo
from mininet.net import Mininet
from mininet.util import dumpNodeConnections
from mininet.log import setLogLevel
from mininet.node import RemoteController

class SimpleNetwork(Topo):
    def __init__(self, **opts):
        Topo.__init__(self, **opts)

        s1 = self.addSwitch('s1')
        s2 = self.addSwitch('s2')
        s3 = self.addSwitch('s3')
        s4 = self.addSwitch('s4')

        h1 = self.addHost('h1', ip='10.0.0.1')
        h2 = self.addHost('h2', ip='10.0.0.2')
        h3 = self.addHost('h3', ip='10.0.0.3')
        h4 = self.addHost('h4', ip='10.0.0.4')

        self.addLink(s1, h1)
        self.addLink(s2, h2)
        self.addLink(s3, h3)
        self.addLink(s4, h4)

        self.addLink(s1, s2)
        self.addLink(s2, s3)
        self.addLink(s3, s4)
        self.addLink(s4, s1)

if __name__=='__main__':
    setLogLevel('info')
    topo = SimpleNetwork()
    net = Mininet(topo, controller=RemoteController('c0', ip='127.0.0.1'))
    net.start()
    net.pingAll()
    net.stop()
```

### CLIの使い方

mininetを起動するとCLIが立ち上がり、コマンドを通して様々指示を送れる。

```sh
>>> pingall          # 全ホスト間でpingを送信し接続を確認する
>>> h1 ping h2       # h1からh2にpingを送る
>>> dpctl dump-flows # 全スイッチのフローエントリーを取得
```

出力したフローエントリーを見ればわかるが、初期状態ではフローエントリーは無い。
したがって、SDNコントローラを用いるなどしてフローエントリーを入力しないと通信は行えない。

### 注意事項

mininetを立ち上げると入力したIPアドレスにコントローラを探しにいく。
したがって、先にコントローラを立ち上げておかないと```Unable to contact the remote controller```とエラーが出る。
コントローラとの接続ポートはデフォルトで6633を使うので、そのポートがあいているかも確認が必要。

### 参考HP

- [mininet walkthrough](http://mininet.org/walkthrough/)
- [mininet sample workflow](http://mininet.org/sample-workflow/)
- [mininetの使い方について(1)](http://www.cloudcluster.cloudysunny14.org/show_materials?id=ahBzfm9uY2xvdWRjbHVzdGVyciYLEg9NYXRlcmlhbHNUaGVtZXMY0YwBDAsSCE1lbnRpb25zGOkHDA)
