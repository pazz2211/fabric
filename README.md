# Hyperledger Fabric

[![Build Status](https://dev.azure.com/Hyperledger/Fabric/_apis/build/status/Merge?branchName=main)](https://dev.azure.com/Hyperledger/Fabric/_build/latest?definitionId=51&branchName=main)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/955/badge)](https://bestpractices.coreinfrastructure.org/projects/955)
[![Go Report Card](https://goreportcard.com/badge/github.com/hyperledger/fabric)](https://goreportcard.com/report/github.com/hyperledger/fabric)
[![GoDoc](https://godoc.org/github.com/hyperledger/fabric?status.svg)](https://godoc.org/github.com/hyperledger/fabric)
[![Documentation Status](https://readthedocs.org/projects/hyperledger-fabric/badge/?version=latest)](http://hyperledger-fabric.readthedocs.io/en/latest)

This project is a _Graduated_ Hyperledger project. For more information on the history of this project see the [Fabric wiki page](https://wiki.hyperledger.org/display/fabric). Information on what _Graduated_ entails can be found in
the [Hyperledger Project Lifecycle document](https://tsc.hyperledger.org/project-lifecycle.html).
Hyperledger Fabric is a platform for distributed ledger solutions, underpinned
by a modular architecture delivering high degrees of confidentiality,
resiliency, flexibility and scalability. It is designed to support pluggable
implementations of different components, and accommodate the complexity and
intricacies that exist across the economic ecosystem.

Hyperledger Fabric delivers a uniquely elastic and extensible architecture,
distinguishing it from alternative blockchain solutions. Planning for the
future of enterprise blockchain requires building on top of a fully-vetted,
open source architecture; Hyperledger Fabric is your starting point.

## Releases

Fabric provides periodic releases with new features
and improvements. Additionally, certain releases are designated as long-term
support (LTS) releases. Important fixes will be backported to the most recent
LTS release, and to the prior LTS release during periods of LTS release overlap.
For more details see the [LTS strategy](https://github.com/hyperledger/fabric-rfcs/blob/main/text/0005-lts-release-strategy.md).

LTS release:
- [v2.2.x](https://hyperledger-fabric.readthedocs.io/en/release-2.2/whatsnew.html) (current LTS release)

Prior LTS release:
- [v1.4.x](https://hyperledger-fabric.readthedocs.io/en/release-1.4/whatsnew.html) (maintenance ended in April 2021 with the delivery of v1.4.12)

Unless specified otherwise, all releases will be upgradable from the prior minor release.
Additionally, each LTS release is upgradable to the next LTS release.

Fabric releases and release notes can be found on the [GitHub releases page](https://github.com/hyperledger/fabric/releases).

Please visit the [GitHub issues with Epic label](https://github.com/hyperledger/fabric/labels/Epic) for our release roadmap.

## Hướng dẫn cài đặt với Ubuntu 20.04
Hướng dẫn cài đặt dưới đây được thực hiện với:
- Ubuntu 20.04
- Hyperledger Fabric 2.4.7

## Prerequisites
<h3>Update và upgrade apt:</h3>
<samp>sudo apt-get update -y </samp> 
</br> <samp> sudo apt upgrade -y </samp>

<h3>Cài đặt các phần mềm:</h3>
<b>GIT</b>
</br><samp>&emsp;sudo apt-get install git -y</samp>

</br><b>cURL</b>
</br><samp>&emsp;sudo apt-get install curl -y</samp>

<b>Docker</b>
</br><samp>&emsp;sudo apt-get -y install docker-compose</samp>

<b> Kiểm tra đã cài đặt thành công Docker hay chưa:</b>
</br><samp>&emsp;docker --version</samp>
</br><samp>&emsp;docker-compose --version</samp>

<b> Chạy Docker và thiết lập chạy cùng hệ thống</b>
</br><samp>&emsp;sudo systemctl start docker</samp>
</br><samp>&emsp;sudo systemctl enable docker</samp>

<b> Tạo group docker, thêm người dùng vào group docker</b>
</br><samp>&emsp;sudo groupadd docker</samp>
</br><samp>&emsp;sudo usermod -aG docker ${USER}</samp>

<b> Đăng xuất, đăng nhập lại hoặc khởi động lại, sau đó chạy đoạn lệnh sau để kiểm tra</b>
</br><samp>&emsp;docker run hello-world</samp>
</br><samp>&emsp;docker ps -a</samp>

<b> Các text editor (nếu cần), máy thật thì dùng lệnh trên, máy ảo dùng lệnh dưới</b>
</br><samp>&emsp;sudo apt-get install code</samp>
</br><samp>&emsp;sudo snap install code --classic</samp>

<h3>Cài đặt các phần mềm hỗ trợ ngôn ngữ Hyperledger Fabric sử dụng, chúng ta có Node, Javascript, Go, Java</h3>
<b> NodeJS 10.19.0 và npm</b>
</br><samp>&emsp;curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -</samp>
</br><samp>&emsp;sudo npm install npm@5.6.0 -g</samp>

</br><b> Go 1.19.2</b>
</br>Xoá các phiên bản cũ nếu có
</br><samp>&emsp;sudo apt remove 'golang-*'</samp>

Tải bản go 1.19.2 bằng wget
</br><samp>&emsp;wget https://go.dev/dl/go1.19.2.linux-amd64.tar.gz</samp>

Giải nén và copy đến thư mục phát triển
</br><samp>&emsp;tar xf go1.19.2.linux-amd64.tar.gz</samp>
</br><samp>&emsp;sudo mv go /usr/local/go-1.19</samp>

<b>  Thiết lập biến môi trường</b>
</br>Mở file bashrc để thêm script
</br><samp>&emsp;sudo nano ~/.bashrc</samp>

<b>  Copy và thêm đoạn lệnh sau vào cuối file (Ctrl + O để lưu, Ctrl + X để thoát)</b>
</br><samp>&emsp;export GOROOT=/usr/local/go-1.19</samp>
</br><samp>&emsp;export PATH=$GOROOT/bin:$PATH</samp>

Áp dụng
</br><samp>&emsp;source ~/.bashrc</samp>

<b>Kiểm tra xem đã cài đặt go được chưa</b>
</br><samp>&emsp;which go</samp>
</br><samp>&emsp;go version</samp>

<b>Javascript</b>
</br><samp>&emsp;sudo apt-get install jq</samp>

<b>java</b>
</br><samp>&emsp;Chưa vui chưa thêm =)) to be continued</samp>

<h3>Tải và cài đặt Hyperledger Fabric</h3>
<b>Tạo root project cho người lập trình Go, nhớ thay github_userid bằng tên github của mình (hoặc tên bất kỳ cũng đượcc nha)</b>
</br><samp>&emsp;mkdir -p $HOME/go/src/github.com/<github_userid></samp>
</br><samp>&emsp;cd $HOME/go/src/github.com/<github_userid></samp>

</br><b>Tải fabric-samples, docker images và binaries</b>
</br><samp>&emsp;curl -sSL https://bit.ly/2ysbOFE | bash -s</samp>

(Optional) Nếu chỉ cần fabric-samples thì clone từ git của Hyperledger
</br><samp>&emsp;git clone https://github.com/hyperledger/fabric-samples</samp>

<b>  Như vậy chúng ta đã cài đặt xong Prerequistes - các phần mềm tiền xử lý để có thể chạy hệ thống mạng Hyperledger Fabric. Dưới đây là hướng dẫn sử dụng các ứng dụng mẫu trong fabric-samples</b>

## Cài đặt ứng dụng mẫu trong fabric-samples
<h3>Xây dựng hệ thống mạng test-network</h3>
<b>Truy cập thư mục chứa test-network, chạy file network.sh</b>
</br><samp>&emsp;cd $HOME/go/src/github.com/<github_userid>/fabric-samples/test-network</samp>
</br><samp>&emsp;./network.sh down</samp>
</br><samp>&emsp;./network.sh up</samp>

</br><b>network.sh up sẽ chạy phương thức up, dựng các peer và orderer đã được thiết lập sẵn trong file, sau khi thực hiện có thể kiểm tra các node đã chạy bằng cách kiểm tra các docker container đang chạy</b>
</br><samp>&emsp;docker ps -a</samp>

<h3>Sử dụng ứng dụng fabcar</h3>
<b>Truy cập thư mục chứa fabcar, chạy file startFabric.h với đối số tương ứng ngôn ngữ mình muốn</b>
</br><samp>&emsp;cd $HOME/go/src/github.com/<github_userid>/fabric-samples/fabcar</samp>
</br><samp>&emsp;./startFabric.sh javascript</samp>

</br><b>Truy cập thư mục của phần mềm sử dụng ngôn ngữ vừa chọn và cài đặt môi trường</b>
</br><samp>&emsp;cd javascript</samp>
</br><samp>&emsp;npm install</samp>

<b>Sau khi cài đặt xong sẽ có 4 file .js, tương ứng 4 câu lệnh: </b>
</br>&emsp;&emsp;enrollAdmin (thêm admin vào ví)
</br>&emsp;&emsp;registerUser (thêm user vào ví)
</br>&emsp;&emsp;invoke (thêm giao dịch/tài sản lên sổ cái)
</br>&emsp;&emsp;query (truy vấn thông tin trên sổ cái)
</br></br><b>Lần lượt gõ các lệnh sau để thử nghiệm</b>
</br><samp>&emsp;node enrollAdmin</samp>
</br><samp>&emsp;node registerUser</samp>
</br><samp>&emsp;node invoke</samp>
</br><samp>&emsp;node query</samp>

## Documentation, Getting Started and Developer Guides

Please visit our
online documentation for
information on getting started using and developing with the fabric, SDK and chaincode:
- [v2.4](http://hyperledger-fabric.readthedocs.io/en/release-2.4/)
- [v2.3](http://hyperledger-fabric.readthedocs.io/en/release-2.3/)
- [v2.2](http://hyperledger-fabric.readthedocs.io/en/release-2.2/)
- [v2.1](http://hyperledger-fabric.readthedocs.io/en/release-2.1/)
- [v2.0](http://hyperledger-fabric.readthedocs.io/en/release-2.0/)
- [v1.4](http://hyperledger-fabric.readthedocs.io/en/release-1.4/)
- [v1.3](http://hyperledger-fabric.readthedocs.io/en/release-1.3/)
- [v1.2](http://hyperledger-fabric.readthedocs.io/en/release-1.2/)
- [v1.1](http://hyperledger-fabric.readthedocs.io/en/release-1.1/)
- [main branch (development)](http://hyperledger-fabric.readthedocs.io/en/latest/)

It's recommended for first-time users to begin by going through the Getting Started section of the documentation in order to gain familiarity with the Hyperledger Fabric components and the basic transaction flow.

## Contributing

We welcome contributions to the Hyperledger Fabric project in many forms.
There’s always plenty to do! Check [the documentation on how to contribute to this project](http://hyperledger-fabric.readthedocs.io/en/latest/CONTRIBUTING.html)
for the full details.

## Community

[Hyperledger Community](https://www.hyperledger.org/community)

[Hyperledger mailing lists and archives](http://lists.hyperledger.org/)

[Hyperledger Discord Chat](https://discord.com/invite/hyperledger)

[Hyperledger Fabric Issue Tracking (GitHub Issues)](https://github.com/hyperledger/fabric/issues)

[Hyperledger Fabric Wiki](https://wiki.hyperledger.org/display/Fabric)

[Hyperledger Wiki](https://wiki.hyperledger.org/)

[Hyperledger Code of Conduct](https://wiki.hyperledger.org/display/HYP/Hyperledger+Code+of+Conduct)

[Community Calendar](https://wiki.hyperledger.org/display/HYP/Calendar+of+Public+Meetings)

## License <a name="license"></a>

Hyperledger Project source code files are made available under the Apache License, Version 2.0 (Apache-2.0), located in the [LICENSE](LICENSE) file. Hyperledger Project documentation files are made available under the Creative Commons Attribution 4.0 International License (CC-BY-4.0), available at http://creativecommons.org/licenses/by/4.0/.


