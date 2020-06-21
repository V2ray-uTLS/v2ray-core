# About

This project is a fork of v2ray, with tls module replaced by [utls](https://github.com/refraction-networking/utls) in order to simulate the fingerprint of popular web browsers.

***Note: NO WARRANT FOR ANY KIND OF USAGE. DO NOT FILE ANY ISSUE. MAY NOT UPDATE ANYMORE.***

## Windows Build

- Install Go
- ```git clone https://github.com/V2ray-uTLS/v2ray-core.git```
- ```cd v2ray-core```
- ```go get github.com/V2ray-uTLS/websocket@master```
- ```mkdir build```
- ```go build -o build\wv2ray.exe -ldflags "-H windowsgui -s -w -X v2ray.com/core.codename=utls -X v2ray.com/core.build=V2ray-uTLS  -X v2ray.com/core.version=4.25.0" .\main\```

## Usage

Note: Use **ONLY** on client.

- Update V2rayN to 3.18 or above.
- Update ```v2ctl.exe``` in your V2rayN folder to 4.25.0 or above.
- Delete ```v2ray.exe``` in your V2rayN folder. Because V2rayN will use ```v2ray.exe``` instead of ```wv2ray.exe``` sometimes.
- Replace ```wv2ray.exe``` in your V2rayN folder.
- Enjoy!

## Details

For tls in v2ray, [Chrome 72 ClientHello](https://tlsfingerprint.io/id/bbf04e5f1881f506) is used.

However, this fingerprint has http/2 as well as http/1.1 in ALPN. If the server supports http/2, they will negotiate the protocol as http/2, which has not been supoorted by the go websocket yet.

So, ws+tls will use [another popular fingerprint](https://tlsfingerprint.io/id/58b1a38e124153a0) which has no http/2 in ALPN extention.

## License

For v2ray part of code: [The MIT License (MIT)](https://raw.githubusercontent.com/v2ray/v2ray-core/master/LICENSE)

For my part of code: [DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE](http://www.wtfpl.net/txt/copying/)
