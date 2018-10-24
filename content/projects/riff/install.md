# 安装riff

## 安装CLI

### Linux

在ubuntu16.04上安装：

```bash
sudo wget -q -O - https://raw.githubusercontent.com/starkandwayne/homebrew-cf/master/public.key | apt-key add -
sudo echo "deb http://apt.starkandwayne.com stable main" | tee /etc/apt/sources.list.d/starkandwayne.list
sudo apt-get update
sudo apt-get install riff
```

也可以直接下载安装，下载地址： https://github.com/projectriff/riff/releases

```bash
curl -Lo riff-linux-amd64.tgz https://github.com/projectriff/riff/releases/download/v0.1.1/riff-linux-amd64.tgz
tar xvzf riff-linux-amd64.tgz
sudo mv riff /usr/local/bin/
```

