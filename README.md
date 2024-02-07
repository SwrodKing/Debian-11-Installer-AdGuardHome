# Debian 11 安装 AdGuardHome
![img](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/Logo-Adguard-150x150.png)
作者：Aymeric Cucherousset

参考[Debian 11 安装程序 AdGuardHome - Aymeric CUCHEROUSSET --- Debian 11 Installer AdGuardHome - Aymeric CUCHEROUSSET (aymeric-cucherousset.fr)](https://aymeric-cucherousset.fr/debian-11-installer-adguardhome/#pll_switcher)
AdGuardHome 是一个 DNS 服务器，其原理与 PiHole 相同，允许您过滤 DNS 请求。在此过程中，我将解释如何在 Debian 11 (Bullseye) 上安装 AdGuardHome。


## 安装 AdGuardHome 的先决条件：

- Debian 11 机器
- 拥有机器上的超级用户权限（root 或 sudo）

## Debian 11 安装 AdGuardHome：

在开始之前，我们将更新包含 AdGuardHome 的计算机：

```
apt update
```

然后，我们将安装 Curl 包，这将允许我们下载安装程序：

```
apt install curl -y
```

然后我们输入安装命令：

```
curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
```

结果如下：

![Installer AdGuardHome sur Debian 11 - Installation](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-1024x563.png)

然后执行以下命令：

```
# Si vous avec sudo : 
sudo /opt/AdGuardHome/AdGuardHome -s start
# Sinon si vous êtes en utilisateur root
/opt/AdGuardHome/AdGuardHome -s start
```

然后打开 Web 浏览器访问以下 URL http://ip-machine:3000

![Première connexion](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-1-1024x506.png)

为 Web 界面和 DNS 服务配置网络接口：

![Debian 11 Installer AdGuardHome - Configuration des interfaces réseau](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-2-1024x506.png)

创建 AdGuard Home Web 管理的用户帐户：

![Debian 11 Installer AdGuardHome - Création du compte administrateur](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-3-1024x506.png)

检查网络配置是否正确：

![Debian 11 Installer AdGuardHome - Installation](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-4-1024x506.png)

 然后登录：

![Debian 11 Installer AdGuardHome - Connexion](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-6-1024x506.png)

最后，您可以访问 AdGuard Home 仪表板：

![Debian 11 Installer AdGuardHome - Dashboard](https://aymeric-cucherousset.fr/wp-content/uploads/2022/09/installer-adguardhome-sur-debian-11-installation-7-1024x506.png)

然后，您可以修改您的盒子/路由器，以便所有设备都连接到 AdGuard，以便从过滤中受益，否则您将必须更改设备的 DNS 服务器。

如果您的ISP是免费的：您可以在平台http://mafreebox.freebox.fr上修改您盒子的DNS服务器

如果您在 Orange：您必须从 http://192.168.1.1 站点停用您盒子的 DHCP 服务器，并激活 AdGuard Home 上的服务器。

您可以导入阻止列表或正则表达式（如以下正则表达式）来阻止 YouTube 广告：

```
(rr[:digit:]{1}---[:space:]{2}-[:space:]{8}-[A-Za-z0-9_]{4})\.googlevideo\.com
```

官方网站：https://adguard.com/fr/adguard-home/overview.html

>  资料来源：
>
> https://github.com/AdguardTeam/AdGuardHome
