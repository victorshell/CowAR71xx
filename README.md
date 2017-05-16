# CowAR71xx
cow for openwrt on AR71xx

去下载cow_openwrt，传入AR71xx的openwrt路由器的/root目录，编辑/root/.cow/rc，执行“./cow”。Enjoy！

//下载go-mips32源 
git clone https://github.com/gomini/go-mips32.git 
cd go-mips32/src

//配置GO编译参数 
export GOOS=linux 
export GOARCH=mips32le <== Change to mips32 if mips

//执行编译

CGO_ENABLED=0 ./make.bash

cd ..

//创建编译后文件存放文件夹 
sudo mkdir /opt/mipsgo

//复制 
sudo cp -R * /opt/mipsgo

//go工程参数配置 
export GOROOT=/opt/mipsgo 
export PATH=/opt/mipsgo/bin:$PATH

3.编译go程序作为测试

mkdir /opt/slu

cd /opt/slu

vim main.go

//源代码………………………………………………………….

package main

import "fmt"

func main() {
       fmt.Println("hello icoolpy.com")
}
//源代码…………………………………………………
//保存退出
由于以上已经设置了path所以在编译打包go源代码时要直接在要打包的.go程序文件夹下直接执行go build指令即可go build main.go
