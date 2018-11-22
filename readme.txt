○Dockerの初回起動方法(windows10でドメインに参加している前提)

・Hyper-Vを有効化する。
「コントロールパネル＞プログラムと機能＞Windowsの機能の有効化または無効化」からHyper-Vを有効にします。

・Docker for Windowsのインストール
https://store.docker.com/editions/community/docker-ce-desktop-windows

・DockerFileを作成する。
※DockerFileは「https://github.com/ucchi2951/ansible」のDockerFileを参照。

・インストール完了後、PowerShellを管理者実行する。

・docker login

・DockerFileが配置してあるパスに移動
(ex.cd C:\Git\ansible)

・docker build -t my-ansible .

・docker images
・C:\Git\ansible\MyDataのフォルダを作成し、Docker内の/mydataにマウントする。
docker run -dit -v C:\Git\ansible\mydata:mydata my-ansible



○Dockerの2回目以降起動方法


・Powershellを管理者実行する。

・Gitのローカルリポジトリがあるパスに移動。
(ex.cd C:\Git\ansible)

・docker images
・C:\Git\ansible\MyDataのフォルダを作成し、Docker内の/mydataにマウントする。
・docker run -dit -v C:\Git\ansible\mydata:mydata my-ansible

・docker ps -a　でCONTAINER IDを確認。

・docker exec -it [CONTAINER ID] /bin/bash




○ssh接続が何故かできない時。
# ansible -i inventory 172.20.254.247 -m ping

paramiko: The authenticity of host '172.20.254.247' can't be established.
The ssh-rsa key fingerprint is b66459f941b87120f93b29e14de2b714.
Are you sure you want to continue connecting (yes/no)?
yes

↑を実行すると次から出来る時がある。


